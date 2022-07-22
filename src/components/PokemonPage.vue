<template>
  <h1>¿Cual es este Pokemon?</h1>

  <PokemonPicture :pokemonId="1" :mostrarPokemon="true"/>
  <PokemonOptions />
</template>

<script>
import PokemonPicture from "./PokemonPicture.vue";
import PokemonOptions from "./PokemonOptions.vue";

export default {
  name: "PokemonPage",
  data() {
    return {};
  },
  components: {
    PokemonPicture,
    PokemonOptions,
  },
};
</script>

<style>
</style>