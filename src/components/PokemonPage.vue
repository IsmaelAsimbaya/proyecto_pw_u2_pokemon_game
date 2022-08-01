<template>
  <h1 v-if="!pokemonCorrecto">Espere por favor.....</h1>
  <div v-else>
    <h1>¿Cual es este Pokemon?</h1>
    <PokemonPicture :pokemonId="pokemonCorrecto.id" :mostrarPokemon="mostrarPokemon" />
    <PokemonOptions :pokemons="pokemonArr" />
  </div>
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
      pokemonCorrecto: null,
      mostrarPokemon: false,

    };
  },
  components: {
    PokemonPicture,
    PokemonOptions,
  },
  methods: {
    async obtenerPokemonsArreglo() {
      this.pokemonArr = await getPokemonOptions();
      const numeroAleatorio = Math.floor(Math.random() * 4);
      console.log(numeroAleatorio);

      this.pokemonCorrecto = this.pokemonArr[numeroAleatorio];
      console.log(this.pokemonCorrecto);
      //Importar varios metodos de un archivo
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