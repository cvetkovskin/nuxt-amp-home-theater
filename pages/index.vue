<template>
  <div class="container">
    <banner :movies="movies" />

    <div class="content-wrapper">
      <h1 class="title">Trending contents</h1>

      <movie-list :movies="movies" />
    </div>
  </div>
</template>

<script>
import Banner from '@/components/Banner.vue'
import MovieList from '@/components/MovieList.vue'
import { getMovies } from '@/libs/apiClient'

export default {
  components: {
    Banner,
    MovieList
  },

  data() {
    return {
      movies: []
    }
  },

  async asyncData() {
    const movies = []

    for (let i = 1; i < 4; i++) {
      const list = await getMovies('man', 2019, i)

      movies.push(...list.filter(movie => movie.Poster !== 'N/A'))
    }

    return {
      movies
    }
  }
}
</script>

<style lang="scss">
.content-wrapper {
  background: #e9e9e7;
  padding: 50px 80px;

  .title {
    margin-bottom: 40px;
    text-align: center;
  }
}
</style>
