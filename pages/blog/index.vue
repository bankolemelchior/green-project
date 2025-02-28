<script setup lang="ts">
import { formatDate } from '~/utils';

const {data: posts} = await useAsyncData('posts',() => queryCollection('blog').all());
</script>

<template>
    <div>
        <UContainer>
            <UBlogList> 
                <UBlogPost 
                v-for="post in posts" 
                :key="post.id" 
                :title="post.title" 
                :description="post.description"
                :image="post.image"
                :authors="post.auteurs"
                :date="formatDate(post.date)"
                />
            </UBlogList>
        </UContainer>
        <p v-if="posts"> on a {{ posts.length}} posts</p>
        <!-- <pre>{{ {posts} }}</pre> -->
    </div>
</template>

<style scoped></style>