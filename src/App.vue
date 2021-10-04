<template>
  <div id="app">
    <Header :logoImg="require('./assets/img/spotify-logo.png')" :genre="genre" :author="author" @selectedGenre="getSelectedGenre" @selectedAuthor="getSelectedAuthor"/>
    <main>
      <Collection :selectedGenre="selectedGenre" :selectedAuthor="selectedAuthor" @albumData="getData"/>
    </main>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Collection from './components/Collection.vue'


export default {
  name: 'App',
  components: {
    Header,
    Collection
  },
  data() {
    return {
      selectedGenre: "",
      selectedAuthor: "",
      genre: [],
      author: []
    }
  },
  methods: {
    getSelectedGenre(e) {
      this.selectedGenre = e
    },
    getSelectedAuthor(e) {
      this.selectedAuthor = e
    },
    getData(data) {
      data.forEach(e => {
        if(this.genre.includes(e.genre) == false && this.author.includes(e.author) == false) {
          this.genre.push(e.genre);
          this.author.push(e.author)
        }

      });
    }
  }
}
</script>

<style lang="scss">
@import './assets/style/common';
  main {
    @include flex--SB-C;
    background-color: $mainColor100;
    min-height: 100vh;
    padding: $heightHeader 0 0 0;
  }

  @media screen and (max-width: 768px) {
      main {
        align-content: flex-start;
        padding: ($heightHeader + $gapX2) $gap-sm $gap $gap-sm;
      }
  }
</style>
