<template>
  <div class="container">
    <h1 v-if="error.statusCode === 404">Page not found</h1>
    <h1 v-else>An error occurred</h1>
    <NuxtLink to="/">back to Home page</NuxtLink>
  </div>
</template>

<script>
export default {
  props: ['error'],
  layout: 'sidebar' // you can set a custom layout for the error page
}
</script>