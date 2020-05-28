<template>
    <div>
        <v-timeline align-top :dense="true">
            <v-timeline-item v-for="(tl, i) in timeline" :key="i" :color="tl.color" :icon="tl.icon" fill-dot="">
                <v-card :color="tl.color" dark>
                    <v-card-title class="title pb-3 pt-3"><h3 class="title">{{ tl.title }}</h3></v-card-title>
                    <v-card-text class="white text--primary"><p class="pt-3 body-1 mb-0">{{ tl.text }}</p></v-card-text>
                </v-card>
            </v-timeline-item>
        </v-timeline>
    </div>
</template>

<script>
export default {
  name: "EventTimeline",
  props: {
    timeline: {
      type: Array,
      required: true
    }
  }
};
</script>

<style lang="scss" scoped>
</style>