<template>
  <li>
    <v-icon v-on:click="completeItem" color="green">
      {{ icons.mdiCheckBold }}
    </v-icon>
    <span :class="{ 'font-weight-thin': complete }">
      {{ item.title }}
      {{ item.text }}
    </span>
    <v-icon v-on:click="removeItem" color="red">
      {{ icons.mdiDelete }}
    </v-icon>
  </li>
</template>

<script>
  import {
    mdiDelete,
    mdiCheckBold,
  } from '@mdi/js'
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
    },
    data: () => ({
      icons: {
        mdiDelete,
        mdiCheckBold,
      },
    }),
  }
</script>
