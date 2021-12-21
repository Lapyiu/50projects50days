<template>
  <div id="app">
    <progress-container :size="dataList.length" />
  </div>
</template>

<script>
import ProgressContainer from './components/ProgressContainer.vue'

export default {
  name: 'App',
  components: {
    ProgressContainer,
  },
  data() {
    return {
      dataList: [1,2,3,4]
    }
  },
}
</script>

<style>
@import url('https://fonts.googleapis.com/css?family=Muli&display=swap');

:root {
  --line-border-fill: #3498db;
  --line-border-empty: #e0e0e0;
}

* {
  box-sizing: border-box;
}

body {
  background-color: #f6f7fb;
  font-family: 'Muli', sans-serif;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100vh;
  overflow: hidden;
  margin: 0;
}
</style>
