<template>
  <v-row>
    <v-chip v-if="addCount">добавлено: {{ addCount }}</v-chip>
    <v-chip v-if="removeCount" color="red">удалено: {{ removeCount }}</v-chip>
    <v-chip v-if="completeCount" color="green">выполнено: {{ completeCount }}</v-chip>
  </v-row>
</template>

<script>

export default {
  name: "Creator",
    props: [
    'addCount',
    'removeCount',
    'completeCount',
  ],
};
</script>
