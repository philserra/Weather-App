<template>
  <weatherapp />
</template>

<script>
import weatherapp from "./components/weather-app.vue";

export default {
  name: "App",
  components: {
    weatherapp,
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
