<template>
  <div id="app">
    <pm-header></pm-header>
    <router-view></router-view>
    <pm-footer></pm-footer>
  </div>
</template>

<script>
import PmHeader from '@/components/layout/Header'
import PmFooter from '@/components/layout/Footer'

export default {
  name: 'app',
  components: { PmFooter, PmHeader },
  data () {
    return {
    }
  }
}
</script>

<style lang="scss">
@import './scss/main.scss';
</style>
