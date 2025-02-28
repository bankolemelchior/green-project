<script setup lang="ts">
const route = useRoute();
const {data:post} = await useAsyncData('post',() => queryCollection('blog').path(route.path).first());
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
                 </UPageBody>
             </UPage>
        </UContainer>
        
</template>

<style scoped></style>