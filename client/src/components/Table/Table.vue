<template>
   <v-data-table
    :headers="headers"
    :items="items"
    :items-per-page="itemsPerPage ? itemsPerPage : 5"
    class="elevation-1"
  ></v-data-table>
</template>

<script>
export default {
  props: {
    headers: {
      type: Array,
      required: true
    },
    items: {
      type: Array,
      required: true
    },
    itemsPerPage: {
      type: Number,
      default: 5
    }
  }
}
</script>

<style>

</style>
