<template>
  <div class="card" v-if="track && track.album">
    <div class="card-image">
      <figure class="image is-1by1">
        <img :src="track.album.images[0].url" alt="artist">
      </figure>
    </div>
    <div class="card-content">
      <div class="media">
        <div class="media-left">
          <figure class="image is-48x48">
            <img :src="track.album.images[0].url" alt="artist">
          </figure>
        </div>
        <div class="media-content">
          <p class="title is-6"><strong>{{ track.name }}</strong></p>
          <p class="subtitle is-6">{{ track.artists[0].name }}</p>
        </div>
      </div>
      <div class="content">
        <small>{{ track.duration_ms | ms-to-mm }}</small>
        <nav class="level">
          <div class="level-left">
            <button class="button is-primary level-item" @click="selectTrack"><span class="icon is-samll"></span>▶</button>
            <button class="button is-warning level-item" @click="goToTrack(track.id)"><span class="icon is-samll"></span>▶</button>
          </div>
        </nav>
      </div>
    </div>
  </div>
</template>

<script>
  import trackMixin from '@/mixins/track'

  export default {
    name: 'track',
    props: {
      track: {
        type: Object,
        required: true
      }
    },
    mixins: [trackMixin],
    methods: {
      goToTrack (id) {
        if (!this.track.preview_url) { return }

        this.$router.push({ name: 'track-detail', params: { id } })
      }
    }
}
</script>
<style lang="scss" scoped>
</style>
