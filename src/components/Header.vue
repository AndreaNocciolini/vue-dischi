<template>
  <div class="header-container">
    <div class="logo-container">
      <img
        class="header-img-logo" 
        src="../assets/images/Spotify_logo_without_text.png" 
        alt="alt"
      >
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
            width: 4%;
            .header-img-logo {
                width: 100%;
                padding: 0.4em;
            }
        }
    }
</style>