<script setup lang="ts">
const navigations = inject('navigation');
// const navigation = inject<Ref<any[]>>('navigation', ref([]));

const links = [{
  label: 'Home',
  icon: 'simple-icons:homeadvisor',
  to: '/'
}, {
  label: 'Blogs',
  icon: 'simple-icons:mdbook',
  to: '/blog'
}]
</script>

<template>
  <UHeader :links="links">
    <!-- <template #logo>
      <Logo class="w-auto h-6" />
    </template>

    <template #right>
      <UColorModeButton />

      <UButton to="https://github.com/nuxt/ui" target="_blank" icon="i-simple-icons-github" color="gray" variant="ghost" />
    </template>

    <template #panel>
      <UNavigationTree :links="mapContentNavigation(navigation)" />
    </template> -->
    <template #left>
        <NuxtLink to="/">
            <UIcon name="simple-icons:devdotto" class="text-7xl shrink-0"/>
        </NuxtLink>
    </template>

    <template #panel>
        <UNavigationTree :links="links" />
    </template>

    <template #right>
        <UColorModeButton />
    </template>
  </UHeader>
</template>