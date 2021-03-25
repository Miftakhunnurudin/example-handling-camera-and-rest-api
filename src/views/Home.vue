<template>
  <div class="home container">
    <Camera/>
    <Map/>
  </div>
</template>

<script>
// @ is an alias to /src
import Camera from '../components/Camera'
import Map from '../components/Map'

export default {
  name: 'Home',
  components: {
    Camera,
    Map
  }
}
</script>
