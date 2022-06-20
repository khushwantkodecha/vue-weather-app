<template>
  <div class="app_container" :class="`${data ? 'app_container app_container_imaged' : 'app_container'}`">
    <div class="app_search_container">
      <input type="text" v-model="query" />
      <button @click="onSubmit">Search</button>
    </div>
    <ResultView v-if="data" :data="data" />
  </div>
</template>

<script>
import ResultView from './components/ResultView.vue';
import axios from 'axios'

export default {
  name: 'App',
  components: {
    ResultView
  },
  data() {
    return {
      query: "",
      data: null
    }
  },
  methods: {
    onSubmit() {
      if (this.query.length) {
        axios.get(`https://api.openweathermap.org/data/2.5/weather?q=${this.query}&appid=0e20d07828c12e4366775ec6a42e5a16&units=metric`)
          .then(res => this.data = res.data)
          .catch(() => alert('Something went wrong!'))
      }
      else {
        alert('Please enter a city name!')
      }
    }
  }
}
</script>

<style>
* {
  padding: 0;
  margin: 0;
}

body {
  background-image: url('https://cutewallpaper.org/21/weather-background/Wallpaper-MiUI-8-Rainy-Weather-background-Minimal-HD-.png');
  width: 100vw;
  height: 100vh;
  background-position: center;
  background-size: cover;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  display: flex;
  justify-content: center;
  margin-top: 5vh;
  text-align: center;
}

.app_container {
  padding: 1em;
  border-radius: 4px;
}

.app_container_imaged {
  background-image: url('https://img.freepik.com/free-vector/gorgeous-clouds-background-with-blue-sky-design_1017-25501.jpg');
  background-position: center;
  -webkit-box-shadow: 10px 10px 40px -6px rgba(0, 0, 0, 0.75);
  -moz-box-shadow: 10px 10px 40px -6px rgba(0, 0, 0, 0.75);
  box-shadow: 10px 10px 40px -6px rgba(0, 0, 0, 0.75);
  background-size: cover;
}

input[type=text] {
  padding: 5px;
  outline: none;
  border: none;
}

input[type=text]:focus {
  border: none;
  outline: none;
  padding: 5px;
}

button {
  padding: 5px 15px;
  background: #ccc;
  border: 0 none;
  cursor: pointer;
}

.app_search_container {
  margin-top: 1em;
}
</style>
