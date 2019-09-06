<template>
  <div class="app">
    <toolbar />

    <div class="content">
      <nuxt />
    </div>

    <Footer />
  </div>
</template>

<script>
import Toolbar from '@/components/Toolbar.vue'
import Footer from '@/components/Footer.vue'

export default {
  name: 'DefaultLayout',

  components: {
    Toolbar,
    Footer
  }
}
</script>

<style lang="scss">
html {
  font-family: 'Source Sans Pro', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, 'Helvetica Neue', Arial,
    sans-serif;
  font-size: 16px;
  word-spacing: 1px;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  box-sizing: border-box;
  color: #ffffff;
  background: #111;
}

*,
*:before,
*:after {
  box-sizing: border-box;
  margin: 0;
}
</style>
