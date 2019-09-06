<template>
  <div class="container">
    <div class="content-wrapper">
      <h1 class="title">All contents</h1>

      <div class="pagination-wrapper">
        <pagination :current-page="currentPage" :total-items="totalItems" :rows-per-page="rowsPerPage" />
      </div>

      <amp-state
        id="Movies"
        :src="url"
        [src]="'https://www.omdbapi.com/?apikey=7f517297&type=movie&s=man&page=' + currentPage"
      />

      <amp-list
        [src]="Movies.Search"
        [hidden]="interaction ? false : 'hidden'"
        hidden
        width="auto"
        height="570"
        layout="fixed-height"
        class="movie-list"
        v-html="listTemplate"
      />

      <movie-list :movies="movies" [hidden]="interaction ? true : false" />
    </div>
  </div>
</template>

<script>
import MovieList from '@/components/MovieList.vue'
import Pagination from '@/components/Pagination.vue'
import { getMovies, getUrl } from '@/libs/apiClient'

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
      currentPage: 1,
      listTemplate: `
        <template type="amp-mustache">
          <div class="movie">
            <amp-img src="{{Poster}}" width="197" height="310" layout="responsive" alt="a sample poster" />
          </div>
        </template>`
    }
  },

  computed: {
    url() {
      return getUrl('man', this.currentPage)
    }
  },

  async asyncData() {
    const res = await getMovies('man')

    const movies = res.Search

    const totalItems = parseInt(res.totalResults)

    return {
      movies,
      totalItems
    }
  }
}
</script>

<style lang="scss">
.content-wrapper {
  padding: 50px 80px;

  .title {
    margin-bottom: 40px;
    text-align: center;
  }
}

.pagination-wrapper {
  display: flex;
  justify-content: flex-end;
  margin-bottom: 15px;
}

.movie-list {
  div[role='list'] {
    display: flex;
    flex-flow: row wrap;
    justify-content: center;
    width: 100%;
  }
}

@media screen and (max-width: 430px) {
  .content-wrapper {
    padding: 50px 0;
  }
}
</style>
