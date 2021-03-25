<template>
    <div class="camera-modal card p-1 shadow-lg">
        <video ref="video" class="camera-stream"/>
        <div class="d-flex justify-content-center mt-1 button">
            <button class="btn btn-primary"  v-if="isPlayed" @click="closeVideo">Pause</button>
            <button class="btn btn-primary"  v-else @click="playVideo">Play</button>
        </div>
    </div>
</template>

<script>
export default {
  data () {
    return {
      isPlayed: true
    }
  },
  methods: {
    closeVideo: function () {
      this.$refs.video.pause()
      this.isPlayed = false
    },
    playVideo: function () {
      this.$refs.video.play()
      this.isPlayed = true
    }
  },
  mounted () {
    navigator.mediaDevices.getUserMedia({ video: true })
      .then(mediaStream => {
        this.$refs.video.srcObject = mediaStream
        this.$refs.video.play()
      })
      .catch(error => console.error('getUserMedia() error:', error))
  }
}
</script>

<style scoped>
    .camera-modal {
        width: 320px;
        height: 240px;
    }
    .camera-stream {
        width: 100%;
        /* max-height: 80%; */
    }
    .button {
      z-index:10;
      position: absolute;
    }
</style>
