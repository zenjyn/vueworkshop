<template>
  <h1>Pokemon Lister</h1>
  <ul>
    <li v-for="p in pokemon" :key="p.name">
      <PokemonCard :pokemon="p" />
    </li>
  </ul>
</template>

<script>
import PokemonCard from '@/components/PokemonCard.vue';

export default {
  name: 'App',
  components: {
    PokemonCard,
  },
  data() {
    return {
      pokemon: [],
    }
  },
  created() {
    fetch('https://pokeapi.co/api/v2/pokemon')
      .then(response => response.json())
      .then((response) => {
        this.pokemon = response.results
      }).catch(error => {
        console.error(error.message);
      });
  },
}
</script>

<style>
</style>
