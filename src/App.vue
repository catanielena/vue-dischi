<template>
  <div id="app">
    <Header/>
    <main>
      <Collection/>
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
  }
}
</script>

<style lang="scss">
@import './assets/style/common';

</style>
