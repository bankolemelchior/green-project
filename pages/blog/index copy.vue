<script setup lang="ts">
const {data: homepage} = await useAsyncData(() => queryCollection('content').first());
const {data: all} = await useAsyncData(() => queryCollection('content').all());
</script>

<template>
    <div>
        <h1>Page Blog 📰</h1>
        <pre>
            {{ homepage }}
            {{ all }}
        </pre>
        <ContentRenderer v-if="homepage" :value="homepage" />
        <div v-else>Home not found</div>
    </div>
</template>

<style scoped></style>