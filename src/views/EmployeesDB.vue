<template>
  <div>
      <v-data-table
        :headers="headers"
        :items="employees"
        :sort-by="['name', 'salary']"
        :sort-desc="[false, true]"
        multi-sort
        class="elevation-1 mt-5"
        @click:row="selectRow"
      ></v-data-table>
    <v-snackbar
      v-model="snackbar"
    >
      Selected Employee {{ currentRow }}
      <v-btn
        color="yellow"
        text
        @click="snackbar = false"
      >
        Close
      </v-btn>
    </v-snackbar>
  </div>
</template>

<script>
export default {
  data() {
    return {
      currentRow: "",
      snackbar: false,
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
      ],
      employees: []
    };
  },
  mounted() {
    this.axios
      .get("data/employees.json")
      .then(r => {
        this.employees = r.data;
      })
      .catch(e => {
        console.log(e);
      });
  },
  methods: {
    selectRow(row) {
      this.snackbar = true;
      this.currentRow = `${row.name} with salary ${row.salary}`;
    }
  }
};
</script>