<template>
    <div class="main bg-neutral-100">
        <div class="cotainer bg-green-700 py-10">
            <p v-if="$fetchState.pending">Fatching planets...</p>
            <p v-if="$fetchState.error">Error while fatching planets.</p>
            <ul class="text-center flex flex-wrap">
                <li v-for="planet in planets" :key="planet.slug" class="mb-10 basis-1/4">
                    <NuxtLink :to="planet.slug" class="inline-block text-white hover:text-green-300">
                        <img :src="planet.image" :alt="planet.title" class="w-52">{{ planet.title }}
                    </NuxtLink>
                </li>
            </ul>
        </div>
    </div>
</template>

<script>
export default {
    head: {
        title: 'Planets',
        meta: [
            {
                hid: 'description',
                name: 'description',
                content: 'Planets page is created by using nuxt api for testing purpose.'
            },
        ],
    },
    data() {
      return {
        planets: []
      }
    },
    async fetch() {
      this.planets = await fetch(
        'https://api.nuxtjs.dev/planets'
      ).then(res => res.json())
    },
    layout: 'sidebar',
}
</script>