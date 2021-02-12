<template>
  <v-card width="500">
    <v-list-item two-line>
        <v-icon v-on:click="completeItem" color="green">
          {{ icons.mdiCheckBold }}
        </v-icon>
      <v-list-item-content>
        <v-list-item-title :class="{ 'font-weight-thin': complete }">{{ item.title }}</v-list-item-title>
        <v-list-item-subtitle :class="{ 'font-weight-thin': complete }">{{ item.text }}</v-list-item-subtitle>
      </v-list-item-content>
        <v-icon v-on:click="removeItem" color="red">
          {{ icons.mdiDelete }}
        </v-icon>
    </v-list-item>
  </v-card>
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
