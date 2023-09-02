<template lang="pug">
  .page.content
    SearchBar(@search="handleSearch")
    .characters-block(v-for="character in filterSearch" :key="character")
      img(:src="character.image")
      div.characters-name {{ character.name }}
      div.characters-gender {{ character.gender }}
    button.showMore(v-if="hasMore" @click="loadMore") Показать еще
</template>

<script>

import axios from 'axios'
import SearchBar from '@/components/SearchBar.vue'

export default {
  name: 'MainComponent',
  components: {
    SearchBar
  },
  data () {
    return {
      search: '',
      characters: [],
      page: 1,
      hasMore: true
    }
  },
  mounted () {
    this.getCharacters()
  },
  methods: {
    getCharacters () {
      axios.get(`https://rickandmortyapi.com/api/character?page=${this.page}`)
        .then(response => {
          this.characters = this.characters.concat(response.data.results)
          this.hasMore = response.data.info.next !== null
        })
        .catch(error => {
          console.log(error)
        })
    },
    loadMore () {
      this.page++
      this.getCharacters()
    },
    handleSearch (search) {
      this.search = search
    }
  },
  computed: {
    filterSearch () {
      return this.characters.filter(character => {
        return character.name.toLowerCase().includes(this.search.toLowerCase())
      })
    }
  }
}
</script>

<style lang="scss">
.page.content {
  display: flex;
  justify-content: space-around;
  align-items: center;
  flex-direction: column;

  h1 {
    background-color: red;
  }

  img {
    border-radius: 50px;
  }

  .characters-block {
    display: flex;
    justify-content: space-around;
    align-items: center;
    flex-direction: column;
    padding-top: 50px;

    .characters-name,
    .characters-gender {
      font-size: 30px;
      font-family: "American Typewriter";
      padding-top: 10px;
    }
  }

  .showMore {
    background-color: aqua;
    font-size: 30px;
    padding: 10px 20px;
    border-radius: 100px;
    margin-top: 40px;
    margin-bottom: 40px;

    &:hover {
      background-color: darken(aqua, 5%);
      font-size: 35px;
    }
  }
}
</style>
