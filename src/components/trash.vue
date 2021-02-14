<template>
  <v-row
    align="center"
    justify="space-around"
  >
    <v-list >
      <Item
        v-for="todo in trash"
        v-bind:key="todo.id"
        v-bind:item="todo"
        v-bind:isTrash="true"
      />
    </v-list>
  </v-row>
</template>

<script>
import Item from './Item';

export default {
  name: 'Trash',
  components: {
    Item
  },
  props: [
    'trash',
  ],

}
</script>
