<template>
  <div class="movie-list">
    <div v-for="(movie, index) in movies" :key="`movie-poster-${index}`" class="movie">
      <div class="poster">
        <amp-img :src="movie.Poster" width="197" height="310" layout="responsive" alt="a sample poster" />
      </div>
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
  }
}
</script>

<style lang="scss">
.movie-list {
  display: flex;
  flex-flow: row wrap;
  width: 100%;

  .movie {
    width: 150px;
    margin: 10px;

    &:hover {
      box-shadow: 0 0 11px rgba(33, 33, 33, 0.5);
    }
  }
}
</style>
