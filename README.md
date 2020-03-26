### Vue-based project skeleton for a map application by [Geoapify](https://www.geoapify.com)
* The project was created with a help of [Vue CLI](https://cli.vuejs.org).

# STEP 1. Run the application
1. [Clone or download](https://help.github.com/en/github/creating-cloning-and-archiving-repositories/cloning-a-repository) the source code of the application to your computer.
2. Install Node.js if not installed [from Download page](https://nodejs.org/en/download/) or [via package manager](https://nodejs.org/en/download/package-manager/).
3. Run `npm install -g @vue/cli` to install [Vue CLI](https://cli.vuejs.org) globally. Note, `sudo` may require for this operation.
4. Go to the application directory.
5. Run `npm install` to get all dependancies.
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

# STEP 2 - Option 1. Display a map with [Mapbox GL](https://docs.mapbox.com/mapbox-gl-js/api/)

# STEP 2 - Option 2. Display a map with [Leaflet](https://leafletjs.com/)

# STEP 2 - Option 3. Display a map with [OpenLayers](https://openlayers.org)

## Build the application
Run `npm run build` from the application directory to compile and minify the project for production.

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).



