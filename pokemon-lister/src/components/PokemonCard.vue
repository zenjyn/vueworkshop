<template>
  <span>{{ pokemon.name }}</span>
</template>

<script>
export default {
  name: 'PokemonCard',
  props: {
    pokemon: Object,
  },
};
</script>
