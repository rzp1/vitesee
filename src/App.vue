<script setup lang="ts">
// https://github.com/vueuse/head
// you can use this to manipulate the document head in any components,
// they will be rendered correctly in the html results with vite-ssg
useHead({
  title: 'Aaron\'s Blog',
  meta: [
    { name: 'keywords', content: 'Aaron, Aaron\'s Blog, blog' },
    { name: 'description', content: 'Aaron blog that recorded daily life and technology' },
  ],
})
</script>

<template>
  <router-view />
</template>
