<template>
  <div id="app">
    <span v-if="removeCount">
      {{ removeCount }}
    </span>
    <img alt="Vue logo" src="./assets/logo.png">
    <List v-on:remove-item-list="removeFromListCount"/>
  </div>
</template>

<script>
import List from './components/List';

export default {
  name: 'app',
  components: {
    List
  },
  data() {
    return {
      removeCount: 0,
    }
  },
  methods: {
    removeFromListCount() {
      this.removeCount += 1;
    }
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
