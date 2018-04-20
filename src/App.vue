<template>
  <div class = 'md-theme-cyan' id="app">
    <div class="container">
      <SourceSelection v-on:sourceChanged="sourceChanged"></SourceSelection>
      <NewsList v-bind:source="source"></NewsList>
    </div>
  </div>
</template>

<script>
import SourceSelection from './components/SourceSelection'
import NewsList from './components/NewsList'
export default {
  name: 'App',
  components: {
    SourceSelection,
    NewsList
  },
  data () {
    return {
      source: ""
    }
  },
  methods: {
    sourceChanged: function (source) {
      this.source = source;
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 20px;
  margin-left: 20px
}
</style>
