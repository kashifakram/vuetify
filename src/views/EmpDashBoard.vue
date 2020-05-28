<template>
    <div>
      <h1>Employees Dashboard</h1>
      <SalesGraph v-for="sale in sales" :key="`${sale.title}`" :sale="sale" />
      <StatisticCard v-for="stat in statistics" :key="`${stat.title}`" :statistic="stat" />
      <Employees-data-set :employees="employees" @selected-employee="setEmployee" />
      <EventTimeline :timeline="timeline" />
      <v-snackbar v-model="snackbar">
        Employee {{ selectedEmployee.name }} is {{ selectedEmployee.title }}
        <v-btn color="yellow" text @click="snackbar = false">Close</v-btn>
      </v-snackbar>

    </div>
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