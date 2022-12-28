<template>
  <!--<link rel="stylesheet" href="ol3gm.css" type="text/css" />-->
  <div id="app">
    <div id="map"></div>
  </div>
</template>
<script>
/* eslint-disable */
import "ol/ol.css";
import Map from "ol/Map";
import View from "ol/View";
//import { Tile as GoogleLayer } from 'ol/layer';
//import {defaults} from 'olgm/interaction.js';
//import OLGoogleMaps from 'olgm/OLGoogleMaps.js';
import { defaults as defaultControls, ScaleLine } from "ol/control";
import {Tile as TileLayer, Vector as VectorLayer} from 'ol/layer';
import {OSM, Vector as VectorSource} from 'ol/source';
export default {
  async mounted() {
    await this.initiateMap();
    //const recaptchaScript1 = document.createElement("script");
    //const recaptchaScript2 = document.createElement("script");
    //const recaptchaScript3 = document.createElement("script");
    //recaptchaScript1.setAttribute(
    //  "src",
    //  "https://maps.googleapis.com/maps/api/js?key=AIzaSyDkbf5MsXZ7eUqxFouSc0yylfOAjOHfgi4"
    //);
    //document.head.appendChild(recaptchaScript1);
    //recaptchaScript2.setAttribute(
    //  "src",
    //  "https://cdn.jsdelivr.net/npm/ol-google-maps@2.2.3/dist/ol-google-maps.js"
    //);
    //document.head.appendChild(recaptchaScript2);
    //recaptchaScript3.setAttribute(
    //  "src",
    //  "https://cdn.jsdelivr.net/npm/ol@6.0.0/build/ol.js"
    //);
    //document.head.appendChild(recaptchaScript3);
  },
  methods: {
    initiateMap() {
      //var googleLayer = new GoogleLayer();

      // create vector layer
      var source = new VectorSource();
      var vector = new VectorLayer({
        source: source
      });
      // create title layer
      var raster = new TileLayer({
        source: new OSM(),
      });
      // create map with 2 layer
      var map = new Map({
        controls: defaultControls().extend([
          new ScaleLine({
            units: "degrees",
          }),
        ]),
        target: "map",
        layers: [raster, vector/*, googleLayer*/],
        view: new View({
          projection: "EPSG:4326",
          center: [-8.542986, 40.927197], 
          zoom: 16,
        }),
      });
      
      //var olGM = new OLGoogleMaps({map: map}); // map is the ol.Map instance
      //olGM.activate();
    },
  },
};
</script>
<style>
#map {
  position: absolute;
  margin: 0;
  padding: 0;
  height: 100%;
  width: 100%;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
#nav {
  padding: 30px;
}
#nav a {
  font-weight: bold;
  color: #2c3e50;
}
#nav a.router-link-exact-active {
  color: #42b983;
}
</style>