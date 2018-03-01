<template>
  <div id="app">
    <tipCalculator></tipCalculator>
  </div>
</template>

<script>
import tipCalculator from './components/tipCalculator.vue'
export default {
  name: 'app',
  components: {
      tipCalculator
  }
}
</script>

<style lang="scss">
#app {
  font-family: 'Open Sans', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  display: flex;
  justify-content: center;
  padding-top: 2rem;
}

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
