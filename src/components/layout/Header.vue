<template>
  <section class="hero is-success">
    <div class="hero-head">
      <header class="nav">
        <div class="container">
          <div class="nav-left">
            <div class="nav-item">
              <strong>Platzi Music</strong>
            </div>
            <div class="nav-right nav-menu">
              <router-link class="nav-item" :to="{ name: 'search' }">Buscar</router-link>
              <router-link class="nav-item" :to="{ name: 'about' }">Nosotros</router-link>
            </div>
          </div>
        </div>
      </header>
    </div>
    <div class="hero-body">
      <div class="container has-text-centered">
        <h1 class="title">Platzi Music</h1>
        <h2 class="subtitle">Canciones que estan Vue-nisimas!</h2>
        <pm-player></pm-player>
      </div>
    </div>
  </section>
</template>

<script>
  import PmPlayer from '@/components/Player'

  export default {
    components: { PmPlayer }
  }
</script>
