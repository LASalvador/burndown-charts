<template>
  <v-app>
    <v-app-bar
      app
      color="primary"
      dark
    >
      <div class="d-flex align-center">
        <v-img
          alt="Vuetify Logo"
          class="shrink mr-2"
          contain
          src="https://cdn.vuetifyjs.com/images/logos/vuetify-logo-dark.png"
          transition="scale-transition"
          width="40"
        />

        <v-img
          alt="Vuetify Name"
          class="shrink mt-1 hidden-sm-and-down"
          contain
          min-width="100"
          src="https://cdn.vuetifyjs.com/images/logos/vuetify-name-dark.png"
          width="100"
        />
      </div>

      <v-spacer></v-spacer>

      <v-btn
        href="https://github.com/vuetifyjs/vuetify/releases/latest"
        target="_blank"
        text
      >
        <span class="mr-2">Latest Release</span>
        <v-icon>mdi-open-in-new</v-icon>
      </v-btn>
    </v-app-bar>

    <v-main class="small">
      <v-row>
        <v-col
          cols="12"
          xs="12"
          sm="12"
        >
          <AmountTable
            :items="desserts"
            :headers="headers"
          />
        </v-col>
        <v-col
          cols="12"
          xs="12"
          sm="12"
        >
           <ListChart
              :chart-data="datacollection"
              :height="130"
            />
        </v-col>
        <v-col
          cols="12"
        >
          <button @click="fillData()">Randomize</button>
        </v-col>
      </v-row>
    </v-main>
  </v-app>
</template>

<script>
import ListChart from './components/ListChart/ListChart'
import AmountTable from './components/AmountTable/AmountTable'

export default {
  name: 'App',

  components: {
    ListChart,
    AmountTable
  },

  data: () => ({
    datacollection: null,
    headers: [
      {
        text: 'Dias',
        align: 'start',
        value: 'day'
      },
      {
        text: 'Planejados',
        value: 'plan',
        sortable: false
      },
      {
        text: 'Reais',
        value: 'actual',
        sortable: false
      }
    ],
    desserts: [
      {
        day: 'Dia 1',
        plan: 10,
        actual: 10
      },
      {
        day: 'Dia 2',
        plan: 9,
        actual: 8
      },
      {
        day: 'Dia 3',
        plan: 8,
        actual: 8
      },
      {
        day: 'Dia 4',
        plan: 7,
        actual: 8
      },
      {
        day: 'Dia 5',
        plan: 6,
        actual: 6
      },
      {
        day: 'Dia 6',
        plan: 5,
        actual: 5
      },
      {
        day: 'Dia 7',
        plan: 4,
        actual: 5
      },
      {
        day: 'Dia 8',
        plan: 3,
        actual: 3
      },
      {
        day: 'Dia 9',
        plan: 2,
        actual: 2
      },
      {
        day: 'Dia 10',
        plan: 1,
        actual: 1
      }
    ]
  }),
  computed: {
    array_plan: function () {
      return this.desserts.map((item) => {
        return item.plan
      })
    },
    array_actual: function () {
      return this.desserts.map((item) => {
        return item.actual
      })
    },
    array_label: function () {
      return this.desserts.map((item) => {
        return item.day
      })
    }
  },
  methods: {
    fillData () {
      this.datacollection = {
        labels: this.array_label,
        datasets: [
          {
            label: 'Horas Planejadas',
            backgroundColor: '#f87979',
            data: this.array_plan
          }, {
            label: 'Horas Reais',
            backgroundColor: 'rgb(54, 162, 235)',
            data: this.array_actual
          }
        ]
      }
    },
    getRandomInt () {
      return Math.floor(Math.random() * (50 - 5 + 1)) + 5
    }
  }
}
</script>

<style scoped>
</style>
