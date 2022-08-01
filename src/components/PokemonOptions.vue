<template>
  <div class="option-container">
    <ul>
      <li v-for="pokemon in pokemons" :key="pokemon.id" v-on:click="$emit('eventoEmitido')">{{ pokemon.nombre }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  props: {
    pokemons: {
      type: Array,
      required: true,
    },
  },
};
</script>

<style>
ul {
  list-style: none;
}
li {
  background-color: white;
  border-radius: 5px;
  border: 1px solid rgba(0, 0, 0, 0.2);
  width: 200px;
  margin-bottom: 10px;
  cursor: pointer;
}

li:hover {
  background-color: rgba(0, 0, 0, 0.5);
}

.option-container {
  justify-content: center;
  display: flex;
}
</style>