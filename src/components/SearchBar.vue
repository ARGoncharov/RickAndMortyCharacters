<template lang="pug">
  .search-box
    input(type="text" v-model="searchQuery" @input="search" placeholder="Search for character..." )
    a(href="#")
      i.fas.fa-search
</template>

<script>
export default {
  name: 'SearchBar',
  data () {
    return {
      searchQuery: ''
    }
  },
  methods: {
    search () {
      this.$emit('search', this.searchQuery)
    }
  }
}

</script>

<style lang="scss">
</style>
