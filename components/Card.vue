<template>
  <v-card
    elevation="2"
    :color="bgcolor"
    min-width="180"
    min-height="132"
    class="mb-3"
    dark
  >
    <v-card-title class="font-weight-light">{{ title }}</v-card-title>

    <div v-if="loading" class="text-center">
      <v-progress-circular
        :size="36"
        :width="2"
        color="#FFADE"
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
    bgcolor: {
      default: "#252550",
      type: String
    },
    loading: {
      default: true,
      type: Boolean
    }
  },
  methods: {
    formatCount(value) {
      return `<h1 class="text-center font-weight-bold display-2">${Number(
        value
      ).toFixed(0)}</h1>`;
    }
  }
};
</script>
