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
  ],
  methods: {
    removeFromList(todo) {
      this.$emit('remove-todo', todo);
    },
    toggleItem(todo) {
      this.$emit('toggle-todo', todo);
    },
  }
}
</script>
