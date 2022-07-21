<template>
  <div>
    <input
      id="num"
      type="text"
      v-model="numero"
      placeholder="Ingrese un numero...."
    />
    <button v-on:click="obtenerPokemon">Buscar</button>
  </div>
  <p></p>
  <div>
    <label for="num">{{ name }} </label>
    <br>
    <img v-if="imagen" v-bind:src="imagen" alt="no encontrado" />
  </div>
</template>

<script>
export default {
  name: "Pokemon",
  data() {
    return {
      name: "",
      imagen: null,
      numero: "",
    };
  },
  methods: {
    async obtenerName() {
      const { name } = await fetch(
        "https://pokeapi.co/api/v2/pokemon/" + this.numero
      ).then((r) => r.json());
      this.name = name;
    },
    obtenerImg() {
      this.imagen =
        "https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/" +
        this.numero +
        ".svg";
    },
    obtenerPokemon() {
      this.obtenerName();
      this.obtenerImg();
    },
  },
};
</script>

<style scoped>
label {
  display: block;
  color: white;
  font-size: 20px;
  margin-top: 20px;
  text-transform: uppercase;
}

div {
  align-content: center;
}
</style>