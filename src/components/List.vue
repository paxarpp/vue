<template>
  <v-row
    align="center"
    justify="space-around"
  >
    <v-row>
      <v-card v-if="title || text">
        <v-card-title>{{ title }}</v-card-title>
        <v-card-text>{{ text }}</v-card-text>
      </v-card>
      <input v-model="title" placeholder="название задачи">
      <input v-model="text" placeholder="задача">
      <v-btn
        color="primary"
        v-on:click="pushMessage"
      >
        добавить
      </v-btn>
    </v-row>
    <ol>
      <Item
        v-for="todo in todos"
        v-bind:key="todo.id"
        v-bind:item="todo"
        v-bind:complete="completeTodos.includes(todo.id)"
        v-on:remove="removeFromList"
        v-on:complete="toggleItem"
      />
    </ol>
  </v-row>
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
      completeTodos: [],
    }
  },
  methods: {
    pushMessage() {
      if (this.title && this.text) {
        this.todos.push({title: this.title, text: this.text, id: Date.now()});
        this.title = '';
        this.text = '';
        this.$emit('add-item-list');
      }
    },
    removeFromList(id) {
      this.todos = this.todos.filter(item => id !== item.id);
      this.$emit('remove-item-list');
    },
    toggleItem(id) {
      if (this.completeTodos.includes(id)) {
        this.completeTodos = this.completeTodos.filter(itemId => id !== itemId);
        this.$emit('uncomplete-item-list');
      } else {
        this.completeTodos.push(id);
        this.$emit('complete-item-list');
      }
    }
  }
}
</script>
