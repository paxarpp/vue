<template>
  <v-row>
    <input v-model="title" placeholder="название задачи" />
		<v-divider vertical />
    <input v-model="text" placeholder="задача" />
		<v-divider vertical />
		<v-spacer></v-spacer>
    <v-btn color="primary" v-on:click="pushMessage"> добавить </v-btn>
  </v-row>
</template>

<script>

export default {
  name: "Creator",
  data() {
    return {
      title: "",
      text: "",
    };
  },
  methods: {
    pushMessage() {
      if (this.title && this.text) {
        this.$emit("add-todo", { title: this.title, text: this.text, id: Date.now() });
        this.title = "";
        this.text = "";
      }
    },
  },
};
</script>
<v-row>
        <v-chip v-if="addCount">добавлено: {{ addCount }}</v-chip>
        <v-chip v-if="removeCount">удалено: {{ removeCount }}</v-chip>
        <v-chip v-if="completeCount">выполнено: {{ completeCount }}</v-chip>
      </v-row>