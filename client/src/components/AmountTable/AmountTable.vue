<template>
   <v-data-table
    :headers="headers"
    :items="items"
    :items-per-page="itemsPerPage ? itemsPerPage : 5"
    class="elevation-1"
  >
  <template v-slot:item.plan="{ item }">
    <v-text-field
      label="Planejado"
      type="number"
      :rules="[rules.required, rules.number]"
      v-model="item.plan"
    ></v-text-field>
  </template>
  <template v-slot:item.actual="{ item }">
    <v-text-field
      label="Atual"
      type="number"
      :rules="[rules.required, rules.number]"
      v-model="item.actual"
    ></v-text-field>
  </template>
  </v-data-table>
</template>

<script>
export default {
  data () {
    return {
      rules: {
        required: value => !!value || 'Digite a quantidade de atividades',
        number: value => {
          const pattern = /^\d+$/
          return pattern.test(value) || 'Digite um número positivo'
        }
      }
    }
  },
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
