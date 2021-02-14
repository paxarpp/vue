<template>
  <v-card width="500">
    <v-list-item two-line>
      <v-icon f-if='!isTrash' v-on:click="completeItem" color="green">
        {{ icons.mdiCheckBold }}
      </v-icon>
      <v-divider f-if='!isTrash' class="mx-4" vertical />
      <v-list-item-content>
        <v-list-item-title :class="{ 'font-weight-thin': item.complete }">{{ item.title }}</v-list-item-title>
        <v-list-item-subtitle :class="{ 'font-weight-thin': item.complete }">{{ item.text }}</v-list-item-subtitle>
      </v-list-item-content>
        <v-icon f-if='!isTrash' v-on:click="removeItem" color="red">
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
      'isTrash'
    ],
    methods: {
      removeItem() {
        this.$emit('remove', this.item);
      },
      completeItem() {
        this.$emit('complete', this.item);
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
