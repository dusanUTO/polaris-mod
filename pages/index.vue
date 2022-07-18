<template>
  <div class="main">
    <div class="container max-w-7xl mx-auto px-6 py-20 2xl:p-28 rounded-xl bg-[url('~/static/bg-1.svg')] bg-contain bg-no-repeat bg-white border border-gray-200">
      <h1 class="text-5xl font-medium">Polaris</h1>
      <p class="text-2xl w-full sm:max-w-sm mt-8">Our design system helps us work together to build a great experience for all of Shopify’s merchants.</p>
      <h3 class="text-3xl mt-24 font-medium">Guides</h3>
      <p class="text-2xl w-full sm:max-w-xl mt-8 text-stone-500">Check out these practical guides to help you understand how to design for the Shopify platform using Polaris.</p>
      <div class="grid grid-cols-1 md:grid-cols-2 xl:grid-cols-4 gap-10 mt-10 pb-10 border-b-4 border-gray-100">
        <template>
          <a v-for="item in sectionItems" :key="item.id" :href=item.link :class=linkStyles >{{ item.title }}</a>
        </template>
      </div>
      <div class="grid grid-cols-1 md:grid-cols-2 xl:grid-cols-4 gap-10 my-10">
        <template>
          <div v-for="item in sectionTwoItems" :key="item.id">
            <h4 class="text-2xl mb-4">{{ item.title }}</h4>
            <p class="mb-4">{{ item.desc }}</p>
            <a :href=item.link :class=linkStyles >{{ item.linkText }}</a>
          </div>          
        </template>
      </div>
      <div class="grid grid-cols-1 md:grid-cols-2 gap-10 mt-16 pb-16 border-b-4 border-gray-100">
        <div class="px-5 py-10 md:px-10 bg-stone-100 rounded-md">
          <h6 class="font-medium">What’s new</h6>
          <h4 class="text-2xl mb-4 font-medium">Polaris v9.0.0</h4>
          <p class="mb-4">A new approach to design tokens. Removes Sass functions, mixins, and more for new CSS custom properties and components to ensure you can ship design decisions with consistency and scale.</p>
          <a href="#!" class="text-blue-500 underline">Read all Polaris updates</a>
        </div>
        <div class="px-5 py-10 md:px-10 bg-stone-100 rounded-md">
          <h6 class="font-medium">Blog posts, talks, and events</h6>
          <div class="mt-4">
            <template>
              <div v-for="item in sectionThreeItems" :key="item.id" class="flex mb-4 last:mb-0 ">
                <img :src="require('~/assets/img/'+item.img+'.jpg')" class="w-16 h-16 rounded-2xl mr-4" />
                <div class="flex-col">
                  <a :href=item.link :class=linkStyles >{{ item.linkText }}</a>
                  <div class="flex">
                    <p class="mr-2">Post by</p>
                    <a :href=item.authorLink :class=linkStyles >{{ item.author }}</a>
                  </div>
                </div>
              </div>          
            </template>  
          </div>             
        </div> 
      </div>
      <div class="mt-10">
        <h3 class="text-3xl font-medium mb-3">Resources</h3>
        <p class="w-full md:max-w-2xl">Downloads, links, and third-party tools to help you and your teams learn, draft, design, and build products for Shopify.</p>
        <div class="grid grid-cols-1 md:grid-cols-2 gap-10 mt-20">
          <template>
            <div v-for="item in sectionFourItems" :key="item.id">
              <h5 class="text-2xl">{{ item.title }}</h5>
              <p>{{ item.desc }}</p>
            </div>          
          </template>
        </div>
        <a href="#!" class="block text-blue-500 underline flex-grow-3 mt-10 md:text-center">Browse more resources</a>
      </div>  
    </div>
  </div>
</template>

<script>
export default {
  name: 'IndexPage',

  data() {
    return {
      sectionItems: [
        { link: "#link1", title: "Shopify experience values" },
        { link: "#link2", title: "Page layouts" },
        { link: "#link3", title: "Designing apps for Shopify" },
        { link: "#link4", title: "Internationalization" },
      ],
      sectionTwoItems: [
        { title: "Content", desc: 'Learn how to use language to design a more thoughtful product experience.', linkText: "Read content guidelines", link: "#link1" },
        { title: "Design", desc: 'Find out how we approach the visual elements of our interface with purpose.', linkText: "Read design guidelines", link: "#link2" },
        { title: "Components", desc: 'Use components as building blocks as you develop new products and features.', linkText: "Browse components", link: "#link3" },
        { title: "Patterns", desc: 'Read guidance for crafting patterns in the Shopify admin.', linkText: "Browse experiences", link: "#link4"},
      ],
      sectionThreeItems: [
        { img: "avatar-m", linkText: "Design systems are flawed", link: "#link1", author: "José Torre", authorLink: "#al1" },
        { img: "avatar-m", linkText: "How to create accessible and inclusive product content guidelines", link: "#link2", author: "Shay Perez", authorLink: "#al2" },
        { img: "avatar-f", linkText: "A map for uncovering your assumptions", link: "#link3", author: "Sara Hill", authorLink: "#al3" },
      ],
      sectionFourItems: [
        { title: "React components", desc: "Browse the source code and latest release notes on GitHub." },
        { title: "Figma UI Kit", desc: "Access the Figma UI Kit via the Shopify Figma Community profile." },
        { title: "GraphQL API", desc: "Use the API to build Figma plugins, text editor extensions, or even a completely new site." },
      ],
      linkStyles: ['text-blue-500 underline flex-grow-3'],
    };
  }
};
</script>