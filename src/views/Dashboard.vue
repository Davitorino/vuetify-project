<template>
  <div>
    <h1>Dashboard</h1>
     <v-data-table
      :headers="headers"
      :items="employees"
      :items-per-page="5"
      class="elevation-1"
      @click:row="selectRow"
    />
    <v-snackbar
      v-model="snackbar"
    >
      You have selected {{ currentItem }}
      <template v-slot:action="{ attrs }">
        <v-btn
          color="pink"
          text
          v-bind="attrs"
          @click="snackbar = false"
        >
          Close
        </v-btn>
      </template>
    </v-snackbar>
  </div>
</template>

<script>
import employeesData from '../data/employees.json'

export default {
  data () {
    return {
      currentItem: '',
      snackbar: false,
      headers: [
        { text: 'Employee ID', value: 'id' },
        { text: 'Name', value: 'name' },
        { text: 'Position Title', value: 'title' },
        { text: 'Salary', value: 'salary' },
      ],
      employees: employeesData,
    }
  },
  methods: {
    selectRow(event) {
      this.snackbar = true
      this.currentItem = event.name
    }
  }
}
</script>

<style lang="scss" scoped>

</style>