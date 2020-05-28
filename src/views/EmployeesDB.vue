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
        color="red"
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
          text: "Dessert (100g serving)",
          align: "start",
          sortable: true,
          value: "name"
        },
        { text: "Calories", value: "calories" },
        { text: "Fat (g)", value: "fat" },
        { text: "Carbs (g)", value: "carbs" },
        { text: "Protein (g)", value: "protein" },
        { text: "Iron (%)", value: "iron" }
      ],
      employees: null
    };
  },
  mounted() {},
  methods: {
    selectRow(row) {
      this.snackbar = true;
      this.currentRow = `${row.name} with calories ${row.calories}`;
    }
  }
};
</script>