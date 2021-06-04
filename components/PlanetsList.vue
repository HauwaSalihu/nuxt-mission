<template>
  <div>
    <p v-if="$fetchState.pending">Fetching Planets..</p>
    <p v-else-if="$fetchState.error">Error while Fetching Planets..</p>
    <ul>
      <li v-for="planet in planets" :key="planet.slug">
        <NuxtLink :to="planet.slug"> {{ planet.title }} </NuxtLink>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  layout: 'home',
  async fetch() {
    this.planets = await fetch('https://api.nuxtjs.dev/planets').then((res) =>
      res.json()
    )
  },
  // eslint-disable-next-line vue/order-in-components
  data() {
    return {
      planets: [],
    }
  },
}
</script>
