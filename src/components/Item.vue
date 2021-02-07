<template>
  <li class="item">
    <span class="item_complete_control" v-on:click="completeItem">v</span>
      <span :class="{ item_complete: complete }">
        {{ item.title }}
        {{ item.text }}
      </span>
    <span class="item_remover" v-on:click="removeItem">X</span>
  </li>
</template>

<script>
  export default {
    name: 'Item',
    props: [
      'item',
      'complete'
    ],
    methods: {
      removeItem() {
        this.$emit('remove', this.item.id);
      },
      completeItem() {
        this.$emit('complete', this.item.id);
      }
    }
  }
</script>

<style scoped>
  .item_remover {
    color: red;
    position: absolute;
    top: -5px;
    right: -5px;
    cursor: pointer;
  }
  .item_complete_control {
    color: rgb(0, 255, 106);
    position: absolute;
    top: -5px;
    left: -5px;
    cursor: pointer;
  }
  .item {
    position: relative;
    font-weight: 600;
    width: 500px;
  }
  .item_complete {
    text-decoration-line: line-through;
    font-weight: 100;
  }
</style>
