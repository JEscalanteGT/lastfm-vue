<template>
  <div class="container" v-if="track && track.id">
    <div class="columns">
      <div class="column is-3 has-text-centered">
        <figure class="media-left">
          <p class="image">
            <img :src="track.album.images[0].url" alt="track">
          </p>
          <p>
            <a class="button is-primary is-large"><span class="icon" @click="selectTrack"></span></a>
          </p>
        </figure>
      </div>
      <div class="column is-8">
        <div class="panel">
          <div class="panel-heading">
            <h1 class="title">{{ trackTitle }}</h1>
          </div>
          <div class="panel-block">
            <article class="media">
              <div class="media-content">
                <div class="content">
                  <ul>
                    <li v-for="(v, k) in track"><strong>{{ k }}:</strong><span>{{ v }}</span></li>
                  </ul>
                </div>
              </div>
              <nav class="level">
                <div class="level-left">
                  <a class="level-item"></a>
                </div>
              </nav>
            </article>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
// import trackService from '@/services/track'
import trackMixin from '@/mixins/track'
import { mapState, mapActions, mapGetters } from 'vuex'

export default {
  name: 'track-detail',
  data () {
    return {
      // track: {}
    }
  },
  mixins: [trackMixin],
  computed: {
    ...mapGetters(['trackTitle']),
    ...mapState(['track'])
  },
  created () {
    // const id = this.$route.params.id
    // trackService.getById(id)
    //   .then(res => {
    //     this.track = res
    //   })
    const id = this.$route.params.id
    if (!this.track || !this.track.id || this.track.id !== id) {
      this.getTrackById({ id })
        .then(() => {
          console.log('Track loaded...')
        })
    }
  },
  methods: {
    ...mapActions(['getTrackById'])
  }
}
</script>
<style lang="scss" scoped>
  .columns {
    margin: 20px;
  }
</style>
