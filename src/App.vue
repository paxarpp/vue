<template>
  <v-app>
    <v-navigation-drawer app>
      <Trash
        v-bind:trash="trash"
      />
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
import Trash from './components/trash';
import Creator from './components/creator';
import Chips from './components/chips';

export default {
  name: 'app',
  components: {
    List,
    Trash,
    Creator,
    Chips,
  },
  data() {
    return {
      todos: [],
      trash: [],
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
    removeTodo(todo) {
      this.todos = this.todos.filter(item => todo.id !== item.id);
      this.trash.push(todo);
      this.removeCount += 1;
    },
    toggleTodo(todo) {
      this.todos = this.todos.map(t => {
        if (t.id === todo.id) {
          return { ...t, complete: !todo.complete }
        }
        return t;
      });
      if (todo.complete) {
        this.completeCount -= 1;
      } else {
        this.completeCount += 1;
      }
    },
  }
}
</script>
