<template>
  <div style="width: 80%; height: 600px" id="app">
    <Map4dMap @onMapReady="onMapReady" :options="options1" :id="id" version="2.4"
      accessKey="__YOUR_KEY___" />
    <!-- <Map4dMap :options="options2" id="map4" version="2.4" accessKey="__YOUR_KEY___"/> -->
  </div>
</template>

<script>
import Map4dMap from './components/Map4dMap.vue'

export default {
  name: 'app',
  components: {
    Map4dMap
  },
  data() {
    return {
      options1: {
        center: { lat: 16.072163491469226, lng: 108.22690536081757 },
        zoom: 17,
        controls: false
      },
      options2: {
        center: { lat: 16.072163491469226, lng: 108.22690536081757 },
        zoom: 18,
        controls: true
      },
      id: "map3"
    }
  },
  methods: {
    onMapReady(map, id) {
      console.log(`Map with id: ${id} is ready`)
      //TODO: Map interaction from here      

      let map4d = window.map4d //remove if disable no-undef from eslint

      let centerMap = map.getCamera().getTarget()
      let marker = new map4d.Marker({
        position: centerMap,
        anchor: [0.5, 1.0],
        label: new map4d.MarkerLabel({ text: "Demo Marker", color: "FF00FF", fontSize: 12 })
      })

      // Thêm marker vào bản đồ
      marker.setMap(map)      
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 20px;
}
</style>
