<template>
  <div>
    <headerComp />
    <div class="flex max-w-7xl mx-auto">
      <p v-if="$nuxt.isOffline" class="fixed top-0 left-0 px-10 bg-red-600 text-white">You are OFFLine!</p>
      <p v-if="$nuxt.isOnline" class="fixed top-0 right-0 px-10 bg-yellow-300">You are ONLine!</p>
      <div class="sidebar w-60 bg-green-500 p-10 mr-4">
        <ul class="text-center flex flex-col">
                <li v-for="planet in planets" :key="planet.slug" class="mb-10">
                    <NuxtLink :to="planet.slug" class="inline-block text-white hover:text-green-300">
                        {{ planet.title }}
                    </NuxtLink>
                </li>
            </ul>
      </div>
      <div class="w-full">
      <Nuxt />
      </div>
    </div>
    <footerComp />
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
        },
    }
</script>