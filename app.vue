<script setup lang="ts">
const {data: navigation} = await useAsyncData('navigation', () => queryCollectionNavigation('blog'));

provide('navigation', navigation);

</script>

<template>
  <!-- <pre> {{ navigation }}</pre> -->
    <NuxtLayout>
      <NuxtPage />
    </NuxtLayout>
    
    <UNotifications />
</template>
