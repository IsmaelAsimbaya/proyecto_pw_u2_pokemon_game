<template>
  <!--<Pokemon />-->
  <!--<PokemonPage />-->
  <img src="./assets/logo.png" alt="Vue Logo" />
  <router-view />
  <ComponentePicture/>
  
</template>

<script>
//import Pokemon from "./components/Pokemon.vue";
//import PokemonPage from "./components/PokemonPage.vue";
import AboutPage from "./modulos/pokemon/pages/AboutPage.vue";
import ComponentePicture from "./modulos/pokemon/componentes/ComponentePicture.vue";

export default {
  name: "App",
  components: {
    //Pokemon,
    //PokemonPage,
    AboutPage,
    ComponentePicture
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
