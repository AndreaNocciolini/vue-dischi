<template>
  <div class="main-container">
    <Search />
    <div>
      <div class="mb-3 p-3">
        <select
          id="selectGenre"
          v-model="key"
          class="p-1 bg-select"
          name="selectGenre"
          @change="filteredAlbum($event)"
        >
          <option
            value=""
            disabled
            selected
          >
            Select a genre
          </option>
          <option value="All">
            All
          </option>
          <option value="Rock">
            Rock
          </option>
          <option value="Pop">
            Pop
          </option>
          <option value="Jazz">
            Jazz
          </option>
          <option value="Metal">
            Metal
          </option>
        </select>
      </div>
    </div>
    <div
      v-if="albums"
      class="albums-container row row-cols-5 g-3"
    >
      <div
        v-for="(album, index) in albums"
        :key="index"
        class="col p-3 m-0"
      >
        <div class="bg-album p-3 album-height">
          <img
            class="mb-2"
            :src="album.poster"
            :alt="album.title"
          >
          <h2 class="text-light mb-3 text-uppercase fs-4">
            {{ album.title }}
          </h2>
          <h3 class="text-muted mb-0 fs-4">
            {{ album.author }}
          </h3>
          <h5 class="text-muted fs-5">
            {{ album.year }}
          </h5>
        </div>
      </div>
    </div>
    <div v-else>
      <div class="loading-screen">
        <h1 class="font-weight-bold">
          Loading...
        </h1>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import Search from './Search.vue'

export default {
    name: 'Main',
    component: {
      Search,
    },
    data() {
      return {
        albums: null,
        key: '',
        supp: null,
      }
    },
    mounted() {
      axios.get('https://flynn.boolean.careers/exercises/api/array/music')
      .then((result) => {
              console.log(result.data.response);
              this.albums = result.data.response;
              this.suppAlbums = this.albums
              }
            )
      .catch((error) => {
              console.log(error)
              }
            )
    },
    methods: {
      filteredAlbum(event) {
        this.albums = this.suppAlbums;
        if(event.target.value === "All"){
          return this.albums
        }
        else {
          return this.albums = this.albums.filter((element) => element.genre.includes(event.target.value))
        }
      }
    },
}
</script>

<style lang="scss">
  .main-container {
    width: 100%;
    background-color: #1E2D3B;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    .albums-container {
      width: 70%;
      margin: 0 auto;
    }
  }
  .bg-select {
    color: #18d860;
    background-color: #1E2D3B;
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