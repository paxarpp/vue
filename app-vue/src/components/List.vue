<template>
  <div class="hello">
    <h1>{{ title }}</h1>
    <h1>{{ text }}</h1>
    <input v-model="title">
    <input v-model="text">
    <button v-on:click="pushMessage">добавить</button>
    <ol>
      <Item v-for="todo in todos" v-bind:key="todo.id" v-bind:item="todo" v-on:remove="removeFromList" />
    </ol>
  </div>
</template>

<script>
import Item from './Item';

export default {
  name: 'List',
  components: {
    Item
  },
  data() {
    return {
      title: '',
      text: '',
      todos: [],
    }
  },
  methods: {
    pushMessage() {
      if (this.title && this.text) {
        this.todos.push({title: this.title, text: this.text, id: Date.now()});
        this.title = '';
        this.text = '';
      }
    },
    removeFromList(id) {
      this.todos = this.todos.filter(item => id !== item.id);
      this.$emit('remove-item-list');
    }
  }
}
</script>

<style scoped>
h3 {
  margin: 40px 0 0;
}
</style>
