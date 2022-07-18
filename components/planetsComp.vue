<template>
    <div>
        <p v-if="$fetchState.pending">Fatching planets...</p>
        <p v-if="$fetchState.error">Error while fatching planets.</p>
        <ul class="text-center py-20">
            <li v-for="planet in planets" :key="planet.slug" class="mb-10">
                <NuxtLink :to="planet.slug" class="inline-block text-white hover:text-green-300">
                    <img :src="planet.image" :alt="planet.title" class="max-w-xs">{{ planet.title }}
                </NuxtLink>
            </li>
        </ul>
    </div>
</template>
<script>
  export default {
    data() {
      return {
        planets: []
      }
    },
    async fetch() {
      this.planets = await fetch(
        'https://api.nuxtjs.dev/planets'
      ).then(res => res.json())
    }
  }
</script>