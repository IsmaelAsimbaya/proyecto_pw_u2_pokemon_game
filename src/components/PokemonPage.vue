<template>
  <h1>¿Cual es este Pokemon?</h1>

  <PokemonPicture :pokemonId="1" :mostrarPokemon="false" />
  <PokemonOptions :pokemons="pokemonArr" />
</template>

<script>
import PokemonPicture from "./PokemonPicture.vue";
import PokemonOptions from "./PokemonOptions.vue";

import getPokemonOptions from "@/helpers/obtenerOpcionesPokemon";

//getPokemonOptions()

export default {
  name: "PokemonPage",
  data() {
    return {
      pokemonArr: [],
    };
  },
  components: {
    PokemonPicture,
    PokemonOptions,
  },
  methods: {
    async obtenerPokemonsArreglo() {
      this.pokemonArr = await getPokemonOptions();
      console.log("Impresion desde el PAGE");
      console.log(this.pokemonArr);
    },
  },
  mounted() {
    this.obtenerPokemonsArreglo();
  },
};
</script>

<style>
</style>