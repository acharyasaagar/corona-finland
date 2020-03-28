<template>
  <v-container class="pa-0">
    <v-col class="mb-3 pa-0" cols="12">
      <h2 class="page-title font-weight-bold">NEW CASES:</h2>
    </v-col>
    <v-col cols="12" class="mb-5">
      <v-row>
        <v-col offset="2" offset-sm="1" cols="8" md="3">
          <Card
            title="NEW CONFIRMED"
            :content="newConfirmedCount"
            :loading="loadingConfirmedCount"
          />
        </v-col>
        <v-col offset="2" offset-sm="1" cols="8" md="3">
          <Card
            title="NEW RECOVERED"
            :content="newRecoveredCount"
            :loading="loadingRecoveredCount"
          />
        </v-col>
        <v-col offset="2" offset-sm="1" cols="8" md="3">
          <Card
            title="NEW DEATHS"
            :content="newDeathsCount"
            :loading="loadingDeathsCount"
          />
        </v-col>
      </v-row>
    </v-col>
  </v-container>
</template>

<script>
import axios from "axios";
import Card from "./Card";
export default {
  name: "Total",
  components: { Card },
  data: () => ({
    newConfirmedCount: null,
    newRecoveredCount: null,
    newDeathsCount: null
  }),
  computed: {
    loadingConfirmedCount() {
      return this.newConfirmedCount === null;
    },
    loadingRecoveredCount() {
      return this.newRecoveredCount === null;
    },
    loadingDeathsCount() {
      return this.newDeathsCount === null;
    }
  },
  async created() {
    const { data } = await axios.get("https://api.covid19api.com/summary");
    const finland = data.Countries.filter(d => d.Country === "Finland");
    this.newConfirmedCount = finland[0].NewConfirmed || 0;
    this.newRecoveredCount = finland[0].NewRecovered || 0;
    this.newDeathsCount = finland[0].NewDeaths || "none";
  }
};
</script>
