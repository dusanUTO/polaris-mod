<template>
  <div class="bg-blue-200 p-10">
    <img :src="post.image" :alt="post.title">
    <h1 class="title">{{ post.title }}</h1>
    <p class="description">{{ post.description }}</p>
    <NuxtLink to="/posts" class="inline-block mt-10">back to posts</NuxtLink>
  </div>
</template>

<style>
    h1 {
        font-size: 80px;
        font-weight: 500;
        color:darkblue;
    }
    .description {
        color: blue;
    }
</style>

<script>
  export default {
    async asyncData({ params, $http }) {
      const post = await $http.$get(`https://api.nuxtjs.dev/posts/${params.id}`)
      return { post }
    },
    layout: 'sidebar-posts',
  }
</script>