<template>
  <div id="app">
    <Header :logoImg="require('./assets/img/spotify-logo.png')" :genre="genre" @selected="getSelectedValue"/>
    <main>
      <Collection :selectedValue="selectedValue" @albumData="getGenre"/>
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
      selectedValue: "",
      genre: []
    }
  },
  methods: {
    getSelectedValue(e) {
      this.selectedValue = e
    },
    getGenre(data) {
      data.forEach(e => {
        if(this.genre.includes(e.genre) == false) {
          this.genre.push(e.genre)
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
