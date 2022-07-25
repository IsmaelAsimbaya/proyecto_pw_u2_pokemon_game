<template>
  <!--<Pokemon />-->
  <!--<PokemonPage />-->
  <Ip />
</template>

<script>
import Pokemon from "./components/Pokemon.vue";
import PokemonPage from "./components/PokemonPage.vue";
import Ip from "./components/Ip.vue";

export default {
  name: "App",
  components: {
    Pokemon,
    PokemonPage,
    Ip
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
