<template>
  <div>
    <div class="mb-3 p-3">
      <select
        id="selectGenre"
        v-model="inputSelect"
        class="p-1 bg-select"
        name="selectGenre"
        @change="$emit('doSearch', inputSelect)"
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
</template>

<script>
export default {
  name: 'Search',
  data() {
    return {
      inputSelect : '',
    }
  }
}
</script>

<style lang="scss">
</style>