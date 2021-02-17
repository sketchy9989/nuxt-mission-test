<template>
   <div >
       <img :src="planet.image" alt="">
      <h1 class='title absolute place-self-end top-0 left-8'>{{ planet.title }}</h1>
          <PlanetsList />

  </div>
</template>

<script>
transition: 'bounce'
export default {
    async asyncData({params}) {
        const planet = await fetch(
        `https://api.nuxtjs.dev/planets/${params.slug}`            
        ).then((res) => res.json())
            return {planet}
    },
}
</script>

<style>

</style>