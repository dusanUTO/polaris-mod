<template>
    <div class="main bg-neutral-100">
        <div class="cotainer bg-blue-300 py-10">
            <p v-if="$fetchState.pending">Fatching posts...</p>
            <p v-if="$fetchState.error">Error while fatching posts.</p>
            <ul class="text-center flex flex-wrap">
                <li v-for="post in posts" :key="post.slug" class="mb-10 basis-1/4">
                    <NuxtLink :to="`/posts/${post.id }`" class="inline-block text-white hover:text-blue-500">
                        <img :src="post.image" :alt="post.title" class="w-52 object-cover">{{ post.title }}
                    </NuxtLink>
                </li>
            </ul>
        </div>
    </div>
</template>

<script>
export default {
    head: {
        title: 'Posts',
        meta: [
            {
                hid: 'description',
                name: 'description',
                content: 'Posts page is created by using nuxt api for testing purpose.'
            },
        ],
    },
    data() {
      return {
        posts: []
      }
    },
    async fetch() {
      this.posts = await fetch(
        'https://api.nuxtjs.dev/posts'
      ).then(res => res.json())
    },
    layout: 'sidebar-posts',
}
</script>