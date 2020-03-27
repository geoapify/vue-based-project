<template>
  <div class="map-container" ref="myMap">
    <div class="placeholder">
      <span class="placeholder-text">The map will be displayed here</span>
    </div>
  </div>
</template>

<script>
export default {
  name: "MyMap",
  mounted: function() {
    console.log("Component is mounted");
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.map-container {
  height: 100%;
  width: 100%;
}

.placeholder {
  height: 100%;
  width: 100%;
  display: flex;
  background-color: darkgray;
}

.placeholder .placeholder-text {
  margin: auto;
}
</style>
