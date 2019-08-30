<template>
  <div class="container">
    <div class="content-wrapper">
      <h1 class="title">All contents</h1>

      <div class="pagination-wrapper">
        <pagination :current-page="currentPage" :total-items="totalItems" :rows-per-page="rowsPerPage" />
      </div>
      <movie-list :movies="movies" />
    </div>
  </div>
</template>

<script>
import MovieList from '@/components/MovieList.vue'
import Pagination from '@/components/Pagination.vue'
import { getMovies } from '@/libs/apiClient'

export default {
  components: {
    MovieList,
    Pagination
  },

  data() {
    return {
      movies: [],
      rowsPerPage: 30,
      totalItems: 140,
      currentPage: 1
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

.pagination-wrapper {
  display: flex;
  justify-content: flex-end;
}
</style>
