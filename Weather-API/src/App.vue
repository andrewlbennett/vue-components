<template>
    <div id="app">
        <p> {{ results.current_observation.temp_f }} </p>
    </div>
</template>

<script>
import axios from 'axios';
const url = 'http://api.wunderground.com/api/API_KEY_GOES_HERE/conditions/q/IL/Chicago.json'

export default {
    name: 'App',
    data() {
        return {
            results: []
        }
    },
    mounted() {
        axios.get(url).then(response => {
            this.results = response.data
        })
    }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
