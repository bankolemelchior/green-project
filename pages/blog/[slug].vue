<script setup lang="ts">
const route = useRoute();
const {data:post} = await useAsyncData('post',() => queryCollection('blog').path(route.path).first());
</script>

<template>
    <div>
        <pre>Page: {{post}}</pre>
    </div>
</template>

<style scoped></style>