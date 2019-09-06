<template>
  <footer>
    <div class="footer">
      <div class="credits">
        <span>Made by: <a href="https://github.com/cvetkovskin" target="_blank">Nikola Cvetkovski</a></span>
        <span>
          Banner background image by
          <a
            href="https://pixabay.com/users/BUMIPUTRA-731298/?utm_source=link-attribution&amp;utm_medium=referral&amp;utm_campaign=image&amp;utm_content=2926963"
            target="_blank"
          >
            BUMIPUTRA
          </a>
          from
          <a
            href="https://pixabay.com/?utm_source=link-attribution&amp;utm_medium=referral&amp;utm_campaign=image&amp;utm_content=2926963"
            target="_blank"
          >
            Pixabay
          </a>
        </span>
      </div>
    </div>
  </footer>
</template>

<style lang="scss">
.footer {
  height: 56px;
  width: 100vw;
  display: flex;
  align-items: center;
  justify-content: flex-end;

  .credits {
    display: flex;
    flex-flow: column;

    a {
      color: #fff;
      font-weight: bold;
    }
  }
}
</style>
