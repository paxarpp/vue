<template>
  <v-app>
    <v-navigation-drawer app>

    </v-navigation-drawer>

    <v-app-bar app>
      <Creator
        v-on:add-todo="addTodo"
      />
    </v-app-bar>

    <v-main>
      <v-container fluid>
        <List
          v-bind:todos="todos"
          v-bind:completeTodos="completeTodos"
          v-on:add-todo="addTodo"
          v-on:remove-todo="removeTodo"
          v-on:toggle-todo="toggleTodo"
        />
      </v-container>
    </v-main>

    <v-footer app>
      <v-container fluid>
        <Chips
          v-bind:addCount="addCount"
          v-bind:removeCount="removeCount"
          v-bind:completeCount="completeCount"
        />
      </v-container>
    </v-footer>
  </v-app>
</template>


<script>
import List from './components/List';
import Creator from './components/creator';
import Chips from './components/chips';

export default {
  name: 'app',
  components: {
    List,
    Creator,
    Chips,
  },
  data() {
    return {
      todos: [],
      completeTodos: [],
      removeCount: 0,
      addCount: 0,
      completeCount: 0,
    }
  },
  methods: {
    addTodo(todo) {
      this.todos.push(todo);
      this.addCount += 1;
    },
    removeTodo(id) {
      this.todos = this.todos.filter(item => id !== item.id);
      this.removeCount += 1;
    },
    toggleTodo(id) {
      if (this.completeTodos.includes(id)) {
        this.completeTodos = this.completeTodos.filter(itemId => id !== itemId);
        this.completeCount -= 1;
      } else {
        this.completeTodos.push(id);
        this.completeCount += 1;
      }
    },
  }
}
</script>
