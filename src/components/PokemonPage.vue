<template>
  <h1 v-if="!pokemonCorrecto">Espere por favor.....</h1>
  <div v-else>
    <h1>¿Cual es este Pokemon?</h1>
    <PokemonPicture
      :pokemonId="pokemonCorrecto.id"
      :mostrarPokemon="mostrarPokemon"
    />
    <PokemonOptions
      :pokemons="pokemonArr"
      @eventoEmitido="validarRespuesta($event)"
    />
    <div v-if="mostrarMensaje">
      <h1>{{ mensajeResultado }}</h1>
      <button v-on:click="resetearJuego">NuevoJuego</button>
    </div>
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
      mensajeResultado: "",
      mostrarMensaje: false,
    };
  },
  components: {
    PokemonPicture,
    PokemonOptions,
  },
  methods: {
    async cargaPokemonInicial() {
      this.pokemonArr = await getPokemonOptions();
      const numeroAleatorio = Math.floor(Math.random() * 4);
      console.log(numeroAleatorio);

      this.pokemonCorrecto = this.pokemonArr[numeroAleatorio];
      console.log(this.pokemonCorrecto);
      //Importar varios metodos de un archivo
      console.log("Impresion desde el PAGE");
      console.log(this.pokemonArr);
    },
    validarRespuesta(pokemonSeleccionadoHijo) {
      const idPoke = pokemonSeleccionadoHijo.part1;
      const namePoke = pokemonSeleccionadoHijo.part2;
      console.log("se emitio un evento desde el hijo ");
      console.log(idPoke);
      if (idPoke === this.pokemonCorrecto.id) {
        this.mostrarPokemon = true;
        this.mensajeResultado = `Correcto, ${namePoke}`;
      } else {
        this.mensajeResultado = `Incorrecto, el pokemon correcto es: ${this.pokemonCorrecto.nombre}`;
        console.log("incorrecto");
      }
      this.mostrarMensaje = true;
    },
    resetearJuego() {
      this.pokemonArr = [];
      this.pokemonCorrecto = null;
      this.mostrarPokemon = false;
      this.mensajeResultado = "";
      this.mostrarMensaje = false;
      this.cargaPokemonInicial();
    },
  },
  mounted() {
    this.cargaPokemonInicial();
  },
};
</script>

<style>
</style>