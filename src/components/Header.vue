<template>
  <div class="header-container">
      <div class="logo-container">
          <img src="../assets/images/Spotify_logo_without_text.png" alt="alt">
      </div>
  </div>
</template>

<script>
export default {
    name: 'Header',
}
</script>

<style lang="scss" scoped>
    .header-container {
        display: flex;
        align-items: center;
        justify-content: flex-start;
        width: 100%;
        background-color: #2E3A46;
        .logo-container {
            width: 3%;
            img {
                width: 100%;
                padding: 1em
            }
        }
    }
</style>