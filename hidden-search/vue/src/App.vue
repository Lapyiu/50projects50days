<template>
  <div id="app">
    <search/>
  </div>
</template>

<script>
import Search from './components/search.vue'

export default {
  name: 'App',
  components: {
    Search
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

* {
  box-sizing: border-box;
}

body {
  background-image: linear-gradient(90deg, #7d5fff, #7158e2);
  font-family: 'Roboto', sans-serif;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100vh;
  overflow: hidden;
  margin: 0;
}

</style>
