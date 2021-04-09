### Vue-based project skeleton for a map application by [Geoapify](https://www.geoapify.com)
* The project was created with a help of [Vue CLI](https://cli.vuejs.org).

# STEP 1. Run the application
1. [Clone or download](https://help.github.com/en/github/creating-cloning-and-archiving-repositories/cloning-a-repository) the source code of the application to your computer.
2. Install Node.js if not installed [from Download page](https://nodejs.org/en/download/) or [via package manager](https://nodejs.org/en/download/package-manager/).
3. Run `npm install -g @vue/cli` to install [Vue CLI](https://cli.vuejs.org) globally. Note, `sudo` may require for this operation.
4. Go to the application directory.
5. Run `npm install` to get all dependencies.
6. Run `npm run serve` 
7. Open [http://localhost:8080/](http://localhost:8080/) to view it in the browser. The page will be reloaded automatically when you make changes to the project.

**The page contains only one phrase "The map will be displayed here", that we replace now with a map.**

### Geoapify Map Tiles
Geoapify offers vector and raster map tiles of different styles and colors. 

We use Mapbox style specification that defines the visual appearance of a map: what data to draw, the order to draw it in, and how to style the data when drawing it. 

Visit our documentation page for [Map Tiles](https://apidocs.geoapify.com/docs/maps/map-tiles/map-tiles) to get a map style link for a map.

### Geoapify API key
You will require Geoapify API Key to display a map. Register and get an API key for free on [Geoapify MyProjects](https://myprojects.geoapify.com).

We have a Freemium pricing model. Start using our services now for FREE and extend when you need.

### Text editor
You can use any text editor for writing HTML, CSS, and JavaScript. However, we recommend you try [Visual Studio Code](https://code.visualstudio.com) + [Vetur extension](https://marketplace.visualstudio.com/items?itemName=octref.vetur) to highlight your code.

# STEP 2 - Option 1. Display a map with [MapLibre GL](https://www.npmjs.com/package/maplibre-gl)(an open-source fork of Mapbox GL)

----

In December 2020 the Mapbox GL JS version 2.0 was released under a proprietary license. So Mapbox GL 2.x not under the 3-Clause BSD license anymore. 
The [MapLibre GL](https://github.com/maplibre/maplibre-gl-js) is the official open-source fork of Mapbox GL.

----

1. Go to the application directory.
2. Run `npm i maplibre-gl` to install Mapbox GL library.
3. Modify src/components/MyMap.vue:
* Remove placeholder
* Add Mapbox GL Styles
* Add Mapbox GL Map
```vue
<template>
  <div class="map-container" ref="myMap"></div>
</template>

<script>
import maplibre from 'maplibre-gl';

export default {
  name: "MyMap",
  mounted: function() {
    const myAPIKey = 'YOUR_API_KEY_HERE'; 
    const mapStyle = 'https://maps.geoapify.com/v1/styles/osm-carto/style.json';

    const initialState = {
      lng: 11,
      lat: 49,
      zoom: 4
    };

    const map = new maplibre.Map({
      container: this.$refs.myMap,
      style: `${mapStyle}?apiKey=${myAPIKey}`,
      center: [initialState.lng, initialState.lat],
      zoom: initialState.zoom
    });

    const markerPopup = new maplibre.Popup().setText('Some marker');
    new maplibre.Marker().setLngLat([initialState.lng, initialState.lat]).setPopup(markerPopup).addTo(map);
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
@import '~maplibre-gl/dist/maplibre-gl.css';

.map-container {
  height: 100%;
  width: 100%;
}
</style>
```
4. Replace YOUR_API_KEY_HERE with an API key you've got on [Geoapify MyProjects](https://myprojects.geoapify.com).
5. Set the mapStyle variable to [Map style](https://apidocs.geoapify.com/docs/maps/map-tiles/map-tiles) you want to use. 

# STEP 2 - Option 2. Display a map with [Leaflet](https://leafletjs.com/)

----

The Leaflet library doesn't have native support for vector map tiles. There a number of Leaflet plugins that may help o visualize vector maps. However, none of them is actively supported.

This tutorial contains instructions on how to visualize raster map tiles. Note, that you need in different vector maps you need to take care of high-resolution screens. Use the '@2x' suffix to get high-resolution map tile images.

----

1. Go to the application directory.
2. Run `npm i leaflet` to install Leaflet library.
3. Modify src/components/MyMap.vue:
* Remove placeholder
* Add Leaflet and Mapbox GL Styles
* Add Leaflet map
```vue
<template>
  <div class="map-container" ref="myMap"></div>
</template>

<script>
import L from "leaflet";

export default {
  name: "MyMap",
  mounted: function() {
    const initialState = {
      lng: 11,
      lat: 49,
      zoom: 4
    };

    const map = L.map(this.$refs.myMap).setView([initialState.lat, initialState.lng], initialState.zoom);

    var myAPIKey = 'YOUR_API_KEY_HERE';

    var isRetina = L.Browser.retina;
    var baseUrl = "https://maps.geoapify.com/v1/tile/osm-bright/{z}/{x}/{y}.png?apiKey={apiKey}";
    var retinaUrl = "https://maps.geoapify.com/v1/tile/osm-bright/{z}/{x}/{y}@2x.png?apiKey={apiKey}";
    
    L.tileLayer(isRetina ? retinaUrl : baseUrl, {
      attribution: 'Powered by <a href="https://www.geoapify.com/" target="_blank">Geoapify</a> | © OpenStreetMap <a href="https://www.openstreetmap.org/copyright" target="_blank">contributors</a>',
      apiKey: myAPIKey,
      maxZoom: 20,
      id: 'osm-bright',
    }).addTo(map);
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
@import "~leaflet/dist/leaflet.css";

.map-container {
  height: 100%;
  width: 100%;
}
</style>
```
4. Replace YOUR_API_KEY_HERE with an API key you've got on [Geoapify MyProjects](https://myprojects.geoapify.com).
5. Set the mapStyle variable to [Map style](https://apidocs.geoapify.com/docs/maps/map-tiles/map-tiles) you want to use. 

# STEP 2 - Option 3. Display a map with [OpenLayers](https://openlayers.org)
1. Go to the application directory.
2. Run `npm install ol ol-mapbox-style` to install OpenLayers library and Mapbox map style support.
3. Modify src/components/MyMap.vue:
* Remove placeholder
* Add OpenLayers Styles
* Add OpenLayers map
```vue
<template>
  <div class="map-container" ref="myMap"></div>
</template>

<script>
import olms from 'ol-mapbox-style';
import * as proj from 'ol/proj';

export default {
  name: "MyMap",
  mounted: function() {
    const initialState = {
      lng: 11,
      lat: 49,
      zoom: 4
    };

    const myAPIKey = 'YOUR_API_KEY_HERE';
    const mapStyle = 'https://maps.geoapify.com/v1/styles/osm-carto/style.json';

    olms(this.$refs.myMap, `${mapStyle}?apiKey=${myAPIKey}`).then((map) => {
      map.getView().setCenter(proj.transform([initialState.lng, initialState.lat], 'EPSG:4326', 'EPSG:3857'));
      map.getView().setZoom(initialState.zoom);
    });
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
@import '~ol/ol.css';

.map-container {
  height: 100%;
  width: 100%;
}
</style>
```
4. Replace YOUR_API_KEY_HERE with an API key you've got on [Geoapify MyProjects](https://myprojects.geoapify.com).
5. Set the mapStyle variable to [Map style](https://apidocs.geoapify.com/docs/maps/map-tiles/map-tiles) you want to use. 

## Build the application
Run `npm run build` from the application directory to compile and minify the project for production.

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).



