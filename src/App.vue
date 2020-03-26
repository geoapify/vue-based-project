<template>
  <div id="app">
    <MyMap />
  </div>
</template>

<script>
import MyMap from "./components/MyMap.vue";

export default {
  name: "App",
  components: {
    MyMap
  }
};
</script>

<style>

html, body {
  margin: 0;
  height: 100%;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  width: 100%;
  height: 100%;
}
</style>
