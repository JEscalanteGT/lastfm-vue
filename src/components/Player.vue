<template>
  <div class="content">
    <p class="is-128x128">
      <img v-if="track && track.album" :src="track.album.images[0].url" alt="Track">
    </p>
    <p>
      <strong>{{ track.name }}</strong>
      <small>{{ track.duration_ms | ms-to-mm }}</small>
    </p>
    <p>
      <audio :src="track.preview_url" controls></audio>
    </p>
  </div>
</template>
<script>
import { mapState } from 'vuex'
export default {
  name: 'player',
  data () {
    return {
      // track: {}
    }
  },
  computed: {
    ...mapState(['track'])
  }
  // created () {
  //   this.$bus.$on('set-track', (track) => {
  //     this.track = track
  //   })
  // }
}
</script>
<style lang="scss" scoped>
  img {
    border-radius: 64px;
    width: 128px;
  }
</style>
