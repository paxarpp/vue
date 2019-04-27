<template>
  <li class="item">
    {{ item.title }}
    {{ item.text }}
    <span class="item_remover" v-on:click="removeItem">X</span>
  </li>
</template>

<script>
export default {
  name: 'Item',
  props: [
    'item'
  ],
  methods: {
    removeItem() {
      this.$emit('remove', this.item.id);
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
.item {
  position: relative;
  font-weight: 600;
  width: 500px;
}
</style>
