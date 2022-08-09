<script setup>
import HelloWorld from './components/HelloWorld.vue'
import TheWelcome from './components/TheWelcome.vue'
import Map4dMap from './components/Map4dMap.vue';
</script>

<script>
export default {
  data() {
    return {
      options1: {
        center: { lat: 16.072163491469226, lng: 108.22690536081757 },
        zoom: 17,
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

<template>
  <header>
    <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" />    
    <div class="wrapper">
      <HelloWorld msg="You did it!" />
    </div>
  </header>

  <main>
    <Map4dMap @onMapReady="onMapReady" :options="options1" :id="id" version="2.4"
      accessKey="__YOUR_KEY__" />
    <TheWelcome />
  </main>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
