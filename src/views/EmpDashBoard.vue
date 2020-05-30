<template>
    <v-container>
      <h1>Employees Dashboard</h1>
      <v-row>
        <v-col v-for="sale in sales" :key="`${sale.title}`" cols="12" md="4">
          <SalesGraph  :sale="sale" />
        </v-col>
      </v-row>
      <v-row>
        <v-col v-for="stat in statistics" :key="`${stat.title}`" cols="12" md="6" lg="3">
          <StatisticCard :statistic="stat" />
        </v-col>
      </v-row>
      <v-row>
        <v-col cols="12" md="8">
          <EmployeesDataSet :employees="employees" @selected-employee="setEmployee" />
        </v-col>
        <v-col cols="12" md="4">
          <EventTimeline :timeline="timeline" />
        </v-col>
      </v-row>
      <v-snackbar v-model="snackbar" :left="$vuetify.breakpoint.lgAndUp">
        Employee {{ selectedEmployee.name }} is {{ selectedEmployee.title }}
        <v-btn color="yellow" text @click="snackbar = false">Close</v-btn>
      </v-snackbar>

    </v-container>
</template>

<script>
import EmployeesDataSet from "@/components/EmployeesDataSet.vue";
import SalesGraph from "@/components/SalesGraph.vue";
import StatisticCard from "@/components/StatisticCard.vue";
import EventTimeline from "@/components/EventTimeline.vue";
export default {
  name: "EmpDashBoard",
  components: {
    EmployeesDataSet,
    SalesGraph,
    StatisticCard,
    EventTimeline
  },
  data: () => ({
    employees: [],
    snackbar: false,
    selectedEmployee: {},
    sales: [],
    statistics: [],
    timeline: []
  }),
  methods: {
    setEmployee(employee) {
      this.snackbar = true;
      this.selectedEmployee = employee;
    }
  },
  mounted() {
    this.$axios
      .get("/data/employees.json")
      .then(r => (this.employees = r.data))
      .catch(e => console.log(e));

    this.axios
      .get("/data/statistics.json")
      .then(r => (this.statistics = r.data))
      .catch(e => console.log(e));

    this.axios
      .get("/data/sales.json")
      .then(r => (this.sales = r.data))
      .catch(e => console.log(e));

    this.axios
      .get("/data/timeline.json")
      .then(r => (this.timeline = r.data))
      .catch(e => console.log(e));
  }
};
</script>

<style lang="scss" scoped>
</style>