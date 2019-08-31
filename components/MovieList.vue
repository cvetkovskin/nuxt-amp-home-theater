<template>
  <div class="movie-list">
    <div v-for="(movie, index) in movies" :key="`movie-poster-${index}`" class="movie">
      <amp-img :src="movie.Poster" width="197" height="310" layout="responsive" alt="a sample poster" />
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
  justify-content: center;
  width: 100%;

  .movie {
    width: 185px;
    margin: 10px;

    &:hover {
      box-shadow: 0 0 11px rgba(33, 33, 33, 0.5);
    }
  }
}

@media screen and (max-width: 430px) {
  .movie-list {
    .movie {
      width: 140px;
    }
  }
}
</style>
