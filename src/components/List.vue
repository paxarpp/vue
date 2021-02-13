<template>
  <v-row
    align="center"
    justify="space-around"
  >
    <v-list >
      <Item
        v-for="todo in todos"
        v-bind:key="todo.id"
        v-bind:item="todo"
        v-bind:complete="check(todo.id)"
        v-on:remove="removeFromList"
        v-on:complete="toggleItem"
      />
    </v-list>
  </v-row>
</template>

<script>
import Item from './Item';

export default {
  name: 'List',
  components: {
    Item
  },
  props: [
    'todos',
    'completeTodos'
  ],
  methods: {
    removeFromList(id) {
      this.$emit('remove-todo', id);
    },
    toggleItem(id) {
      this.$emit('toggle-todo', id);
    },
    check(id) {
      return !!this.completeTodos.includes(id);
    }
  }
}
</script>
