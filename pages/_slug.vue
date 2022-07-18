<template>
<div class="main">
    <div class="container p-10">
        <div>
            <img :src="planet.image" alt="">
            <h1 class="title">{{planet.title}}</h1>
            <p class="description">{{planet.description}}</p>
        </div>
            <NuxtLink to="/planets" class="inline-block mt-10">back to planets</NuxtLink>
    </div>
</div>
</template>
<style>
    .container {
        margin: 0 auto;
        text-align: center;
        background: yellowgreen;
    }

    img {
        max-height: 200px;
        margin: 0 auto;
    }
    h1 {
        font-size: 80px;
        font-weight: 500;
        color: white;
    }
    .description {
        max-width: 320px;
        margin: 0 auto;
        color: darkgreen;
    }
</style>
<script>
    export default {
        head() {
            return {                
                title: this.planet.title,
                meta: [
                    {
                        hid: 'description',
                        name: 'description',
                        content: this.planet.description,
                    }
                ],
            }
        },
        async asyncData({params}) {
            const planet = await fetch(
                `https://api.nuxtjs.dev/planets/${params.slug}`
                ).then((res) => res.json())
                return {planet}
        },
        layout: 'sidebar',
    }
</script>