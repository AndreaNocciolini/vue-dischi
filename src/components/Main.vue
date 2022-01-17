<template>
  <div class="main-container">
    <div v-if="albums" class="albums-container row row-cols-5 g-3">
      <div v-for="(album, index) in albums" :key="index" class="col p-3">
        <div class="bg-album p-3 album-height">
          <img class="mb-2" :src="album.poster" :alt="album.title">
          <h2 class="text-light mb-3 text-uppercase fs-4">{{ album.title }}</h2>
          <h3 class="text-muted mb-0 fs-4">{{ album.author }}</h3>
          <h4 class="text-muted fs-5">{{ album.year }}</h4>
        </div>
      </div>
    </div>
    <div v-else>
      <div class="loading-screen">
        <h1 class="font-weight-bold">Loading...</h1>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
    name: 'Main',
    data() {
      return {
        albums: null,
      }
    },
    mounted() {
      axios.get('https://flynn.boolean.careers/exercises/api/array/music')
      .then((result) => {
              console.log(result.data.response);
              this.albums = result.data.response;
              }
            )
      .catch((error) => {
              console.log(error)
              }
            )
    }
}
</script>

<style lang="scss">
  .main-container {
    width: 100%;
    background-color: #1E2D3B;
    .albums-container {
      width: 70%;
      margin: 0 auto;
    }
  }
  img {
    width: 100%;
  }
  .bg-album {
    background-color: #2e3a46;
  }
  .album-height {
    height: 100%;
  }
  .loading-screen {
    height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
  }
</style>