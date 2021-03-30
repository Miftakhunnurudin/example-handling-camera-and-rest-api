<template>
  <div class="map card shadow-lg p-1">
    <MglMap
      :accessToken="mapboxAccessToken"
      :mapStyle.sync="mapStyle"
      :center="coordinates"
      :zoom="3"
    >
      <MglMarker :coordinates="coordinates" color="blue" />
    </MglMap>
    <i class="button bi-geo-alt-fill btn btn-primary" @click="locatorButtonPressed"></i>
  </div>
</template>

<script>
import { MglMap, MglMarker } from 'vue-mapbox'

export default {
  components: {
    MglMap,
    MglMarker
  },
  data () {
    return {
      mapStyle: 'mapbox://styles/mapbox/streets-v11',
      coordinates: [-111.549668, 39.014],
      mapboxAccessToken: 'pk.eyJ1IjoibWlmdGFraHVubnVydWRpbiIsImEiOiJja212eGd1eTIwOWplMm9xaXQ0ejg1c3gzIn0.AF_yunCfiTcgJ-IwuqBLMw'
    }
  },
  methods: {
    locatorButtonPressed () {
      navigator.geolocation.getCurrentPosition(
        position => {
          const { latitude, longitude } = position.coords
          console.log(latitude, longitude)
          this.coordinates = [longitude, latitude]
        },
        error => {
          console.log(error.message)
        }
      )
    }
  }
}
</script>
<style>
  .map {
    width: 320px;
    height: 240px;
  }
  .button {
      z-index:10;
      position: absolute;
    }
</style>
