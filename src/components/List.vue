<template>
  <div>
    <div class="new_todo">
      <div v-if="title || text">
        <h1>{{ title }}</h1>
        <h2>{{ text }}</h2>
      </div>
      <div v-else>
        <h1>Нет данных</h1>
      </div>
    </div>
    <div class="control">
      <input v-model="title" placeholder="название задачи">
      <input v-model="text" placeholder="задача">
      <button v-on:click="pushMessage">добавить</button>
    </div>
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

<style scoped>
  .new_todo {
    width: 500px;
    margin: 0 auto;
    border: 1px solid #80808033;
    border-radius: 4px;
    box-shadow: 6px 7px 10px 0px grey;
  }
  .control {
    width: 420px;
    height: 100px;
    margin: 0 auto;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
</style>
