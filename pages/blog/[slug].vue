<script setup lang="ts">
const route = useRoute();
const {data:post} = await useAsyncData('post',() => queryCollection('blog').path(route.path).first());
const {data:surround} = await useAsyncData(`${route.path}-surround`,() => queryCollectionItemSurroundings('blog', route.path, {fields:['description']}));
</script>

<template>
        <UContainer v-if="post">
            <UPageHeader :title="post.title" :description="post.description" >
                <template #headline>
                    <UBadge v-bind="post.badge" variant="subtle"/>
                    <span class="text-gray-700">&middot;</span>
                    <time :datetime="post.date">{{formatDate(post.date)}}</time>
                </template>

                <div class="flex flex-wrap items-center gap-2 mt-4">
                    <UButton
                    v-for="(auteur, index) in post.auteurs"
                        :key="index"
                        color="white"
                        variant="ghost"
                        :to="auteur.to"
                        target="_blank"
                    >
                    <UAvatar v-bind="auteur.avatar" :alt="`Avatar de ${auteur.name}`"/>
                    {{ auteur.name }}
                    </UButton>
                </div>
            </UPageHeader>
            <!-- Body -->
             <UPage>
                 <UPageBody v-if="post" prose>
                    <ContentRenderer :value="post"/>
                    <!-- séparateur -->
                    <UDivider v-if="surround" class="my-5"/>
                    <!-- Les liens des articles suivants et précédants -->
                     
                     <UContentSurround v-if="surround" :surround="surround"/>
                 </UPageBody>
                 <template #right v-if="post.body.toc?.links.length">
                     <UContentToc :links="post.body.toc?.links" />
                 </template>
             </UPage>
        </UContainer>
        <pre>{{ surround }}</pre>
</template>

<style scoped></style>