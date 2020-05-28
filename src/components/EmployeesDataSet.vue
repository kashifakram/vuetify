<template>
      <v-data-table
        :headers="headers"
        :items="employees"
        :sort-by="['name', 'salary']"
        :sort-desc="[false, true]"
        multi-sort
        class="elevation-1 mt-5"
        @click:row="selectRow"
      ></v-data-table>
</template>

<script>
export default {
  props: {
    employees: {
      type: Array,
      required: true
    }
  },
  data: () => ({
    headers: [
      {
        text: "id",
        align: "start",
        sortable: true,
        value: "id"
      },
      { text: "Name", value: "name" },
      { text: "Position", value: "title" },
      { text: "Salary", value: "salary" }
    ]
  }),
  methods: {
    selectRow(emp) {
      const selectedEmp = {
        name: emp.name,
        title: emp.title
      };
      this.$emit("selected-employee", selectedEmp);
    }
  }
};
</script>

<style lang="scss" scoped>
</style>