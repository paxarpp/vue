<template>
  <div id="app">
    <v-app>
      <v-row
        align="center"
        justify="space-around"
      >
        <span v-if="addCount">
          добавлено: {{ addCount }}
        </span>
        <span v-if="removeCount">
          удалено: {{ removeCount }}
        </span>
        <span v-if="completeCount">
          выполнено: {{ completeCount }}
        </span>
      </v-row>
        <List
          v-on:remove-item-list="removeFromListCount"
          v-on:add-item-list="addListCount"
          v-on:complete-item-list="complete"
          v-on:uncomplete-item-list="uncomplete"
        />
    </v-app>
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
      addCount: 0,
      completeCount: 0,
    }
  },
  methods: {
    removeFromListCount() {
      this.removeCount += 1;
    },
    addListCount() {
      this.addCount += 1;
    },
    complete() {
      this.completeCount += 1;
    },
    uncomplete() {
      this.completeCount -= 1;
    }
  }
}
</script>
