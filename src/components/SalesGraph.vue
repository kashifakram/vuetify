<template>
    <div>
        <v-card :color="sale.color" dark>
            <v-card-text>0
                <v-sparkline
                :value="sale.sales"
                :labels="sale.labels"
                color="rgba(255, 255, 25, .6)"
                height="100"
                padding="24"
                stroke-linecap="round"
                smooth
                />
            </v-card-text>
            <v-card-text class="text-center">
                <div class="display-1">
                    {{ sale.title }}
                </div>    
            </v-card-text>
        </v-card>
    </div>
</template>

<script>
export default {
  name: "SalesGraph",
  props: {
    sale: {
      type: Object,
      required: true
    }
  }
};
</script>

<style lang="scss" scoped>
</style>