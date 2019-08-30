<template>
  <div class="pagination">
    <amp-state id="rowsPerPage">
      <script type="application/json">
        {{ rowsPerPage }}
      </script>
    </amp-state>
    <amp-state id="totalItems">
      <script type="application/json">
        {{ totalItems }}
      </script>
    </amp-state>
    <amp-state id="currentPage">
      <script type="application/json">
        {{ currentPage }}
      </script>
    </amp-state>
    <amp-state id="totalPages">
      <script type="application/json">
        {{ totalPages }}
      </script>
    </amp-state>
    <amp-state id="startItem">
      <script type="application/json">
        {{ rowsPerPage * (currentPage - 1) + 1 }}
      </script>
    </amp-state>
    <amp-state id="endItem">
      <script type="application/json">
        {{ endItem }}
      </script>
    </amp-state>
    <amp-state id="movies" :src="url" />

    <div class="info">
      <span [text]="'Showing ' + startItem + ' - ' + endItem + ' out of ' + totalItems + ' movies'">
        Showing {{ startItem }} - {{ endItem }} out of {{ totalItems }} movies
      </span>
    </div>
    <div class="controls">
      <div
        class="button"
        :class="{ 'is-disabled': currentPage === 1 }"
        [class]="currentPage == 1 ? 'button is-disabled' : 'button'"
        on="tap:AMP.setState({ currentPage: currentPage - 1, startItem: startItem - rowsPerPage, endItem: endItem - rowsPerPage })"
        role="button"
        tabindex="5"
      >
        <fa-icon class="icon" :icon="['fas', 'chevron-left']" />
      </div>
      <div class="button">
        <div class="button-text" [text]="currentPage">
          {{ currentPage }}
        </div>
      </div>
      <div
        class="button"
        :class="{ 'is-disabled': currentPage === totalPages }"
        [class]="currentPage == totalPages ? 'button is-disabled' : 'button'"
        on="tap:AMP.setState({ currentPage: currentPage + 1 , startItem: startItem + rowsPerPage, endItem: totalItems < endItem + rowsPerPage ? totalItems : endItem + rowsPerPage })"
        role="button"
        tabindex="5"
      >
        <fa-icon class="icon" :icon="['fas', 'chevron-right']" />
      </div>
    </div>
  </div>
</template>

<script>
import { library } from '@fortawesome/fontawesome-svg-core'
import { faChevronRight, faChevronLeft } from '@fortawesome/free-solid-svg-icons'
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome'
import { getUrl } from '@/libs/apiClient'

library.add(faChevronRight, faChevronLeft)

export default {
  name: 'Pagination',

  components: {
    faIcon: FontAwesomeIcon
  },

  props: {
    rowsPerPage: {
      type: Number,
      default: 10
    },

    totalItems: {
      type: Number,
      default: 10
    },

    currentPage: {
      type: Number,
      default: 1
    }
  },

  computed: {
    startItem() {
      return (this.currentPage - 1) * this.rowsPerPage + 1
    },

    endItem() {
      const end = this.currentPage * this.rowsPerPage

      return this.totalItems < end ? this.totalItems : end
    },

    totalPages() {
      return Math.ceil(this.totalItems / this.rowsPerPage)
    },

    url() {
      return getUrl('man', 2019, this.currentPage)
    }
  }
}
</script>

<style lang="scss" scoped>
.pagination {
  height: 44px;
  font-size: 16px;
  display: flex;

  .info {
    padding: 12px;
  }

  .controls {
    display: flex;

    .button {
      height: 44px;
      width: 44px;
      text-align: center;
      margin-right: 5px;
      padding: 14px;
      outline: none;

      &-text {
        font-weight: 700;
      }
    }

    .is-disabled {
      pointer-events: none;

      .icon {
        color: #c9c9c9;
      }
    }
  }
}
</style>
