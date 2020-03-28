<template>
  <v-card min-width="180" min-height="150" class="mb-3 text-primary">
    <v-card-title class="text-primary">{{ title }}</v-card-title>
    <v-divider></v-divider>
    <v-col cols="12"></v-col>
    <div v-if="loading" class="text-center">
      <v-progress-circular
        :size="36"
        :width="2"
        indeterminate
      ></v-progress-circular>
    </div>
    <animated-number
      v-if="!loading"
      :value="content"
      :format-value="formatCount"
      :duration="500"
    ></animated-number>
  </v-card>
</template>

<script>
import AnimatedNumber from "animated-number-vue";
export default {
  name: "Card",
  components: {
    AnimatedNumber
  },
  props: {
    title: {
      default: "Error",
      type: String
    },
    content: {
      default: 0,
      type: Number
    },

    loading: {
      default: true,
      type: Boolean
    }
  },
  methods: {
    formatCount(value) {
      return `<h1 class="text-center font-weight-bold display-2 text-primary">${Number(
        value
      ).toFixed(0)}</h1>`;
    }
  }
};
</script>
