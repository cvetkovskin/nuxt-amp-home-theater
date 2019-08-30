<template>
  <div class="app">
    <span>
      <div class="toolbar">
        <div class="items">
          <div class="t-btn" role="button" tabindex="1" on="tap:AMP.navigateTo(url='/')">Home</div>
          <div class="t-btn" role="button" tabindex="2" on="tap:AMP.navigateTo(url='/series')">Series</div>
          <div class="t-btn btn-small" role="button" tabindex="2">
            <fa-icon class="icon" :icon="['fas', 'share-alt']" />
          </div>
        </div>
      </div>
    </span>
    <div class="content">
      <nuxt />
    </div>
    <div class="footer">
      <div class="credits">
        <!-- <img class="logo" src="@/assets/images/themoviedb.png" /> -->
      </div>
    </div>
  </div>
</template>

<script>
import { library } from '@fortawesome/fontawesome-svg-core'
import { faShareAlt } from '@fortawesome/free-solid-svg-icons'
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome'

library.add(faShareAlt)

export default {
  name: 'DefaultLayout',

  components: {
    faIcon: FontAwesomeIcon
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
  color: #35495e;
}

*,
*:before,
*:after {
  box-sizing: border-box;
  margin: 0;
}

.toolbar {
  width: 100vw;
  height: 56px;
  background: transparent;
  display: flex;
  justify-content: flex-end;
  align-items: center;
  position: absolute;
  top: 0;
  z-index: 2;

  .title {
    padding: 13px 10px;
    font-size: 30px;
  }

  .items {
    height: 100%;
    display: flex;
    align-items: center;

    .t-btn {
      margin-left: 5px;
      height: 100%;
      min-width: 80px;
      text-align: center;
      font-size: 16px;
      padding: 20px 0;
      outline: none;

      &:hover {
        border-bottom: 1px solid black;
      }

      &:active {
        border-bottom: 3px solid black;
        font-size: 14px;
        padding: 21px 0;

        .icon {
          height: 14px;
        }
      }

      .icon {
        height: 16px;
      }
    }

    .btn-small {
      min-width: 50px;
    }
  }
}

.footer {
  position: fixed;
  bottom: 0;
  height: 56px;
  width: 100vw;
  display: flex;
  justify-content: flex-end;

  .credits {
    height: 100%;

    .logo {
      height: 100%;
    }
  }
}
</style>
