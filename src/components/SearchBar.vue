<template lang="pug">
  .search-box
    input(type="text" v-model="searchTerm" placeholder="Search for character..." )
    a(href="#" @click="search")
      i.fas.fa-search
</template>

<script>
export default {
  name: 'SearchBar',
  data () {
    return {
      searchTerm: ''
    }
  },
  methods: {
    search () {
      this.$emit('search', this.searchTerm)
    }
  }
}

</script>

<style lang="scss" scoped>

.search-box {
  height: 30px;
  display: flex;
  cursor: pointer;
  padding: 10px 20px;
  background: #fff;
  border-radius: 30px;
  align-items: center;
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.3);

  &:hover input {
    width: 400px;
  }

  input {
    width: 0;
    outline: none;
    border: none;
    font-weight: 500;
    transition: 0.5s;
    background: transparent;
  }

  i.fas {
    color: aquamarine;
    font-size: 20px;
  }
}

</style>
