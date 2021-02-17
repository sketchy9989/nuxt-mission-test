<template>
  <div>

   <div v-if="$fetchState.pending" class="flex">
     <p  class="text-3xl mx-auto">Fetching planets...</p>
   </div>
   <div v-else-if="$fetchState.error" class="flex">
     <p class="mx-auto text-xl">Error while fetching planets...</p>
     </div>     
     <ul v-else>
       <li v-for='planet in planets' :key='planet.slug'>
         <nuxt-link :to='planet.slug' class='link'>{{planet.title}}</nuxt-link>
       </li>
     </ul>
  

  </div>
</template>

<script>
export default {
async fetch() {
    this.planets = await fetch('https://api.nuxtjs.dev/planets').then((res) => res.json())
  },
  data() {
    return {
      planets: []
    }
  },
}
</script>

<style>

</style>