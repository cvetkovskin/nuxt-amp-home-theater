<template>
  <div class="row banner">
    <div class="title-logo">
      <amp-img width="1048" height="200" layout="responsive" :src="appLogo" />
    </div>
    <div class="nuxt-logo">
      <amp-img width="300" height="220" layout="responsive" :src="nuxtLogo" />
    </div>
    <div class="amp-logo">
      <amp-img width="256" height="256" layout="responsive" :src="ampLogo" />
    </div>
    <div class="banner-carousel">
      <amp-carousel width="197" height="310" layout="responsive" type="slides" autoplay delay="2000">
        <amp-img
          v-for="(movie, index) in movies"
          :key="`movie-poster-${index}`"
          :src="movie.Poster"
          width="197"
          height="310"
          layout="responsive"
          alt="a sample poster"
        />
      </amp-carousel>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    movies: {
      type: Array,
      default: () => []
    }
  },

  data() {
    return {
      appLogo: require('@/assets/images/title-logo.png'),
      nuxtLogo: require('@/assets/images/nuxt-logo.png'),
      ampLogo: require('@/assets/images/amp-logo.svg')
    }
  }
}
</script>

<style lang="scss">
.row {
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;

  .col {
    width: 20vw;
    height: 20%;
  }
}

.banner {
  height: calc(100vw * 1289 / 1920);
  background-image: url('~@/assets/images/banner.jpg');
  background-repeat: no-repeat;
  background-size: cover;
  position: relative;

  &-carousel {
    width: 23vw;
    position: absolute;
    top: 5.9%;
    right: 25%;
  }

  .title-logo {
    height: 10%;
    width: 40vw;
    position: absolute;
    top: 10%;
    left: 5%;
  }

  .nuxt-logo {
    left: 28%;
    width: 10vw;
    bottom: 27%;
    position: absolute;
  }

  .amp-logo {
    left: 37.5%;
    width: 8vw;
    bottom: 27%;
    position: absolute;
  }
}

.amp-carousel-button {
  display: none;
}
</style>
