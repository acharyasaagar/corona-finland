<template>
  <v-container class="pa-0">
    <v-col class="mb-3 pa-0" cols="12">
      <h2 class="page-title font-weight-bold">TOTAL CASES:</h2>
    </v-col>
    <v-col cols="12" class="mb-5">
      <v-row>
        <v-col offset="2" offset-sm="1" cols="8" md="3">
          <Card
            title="CONFIRMED"
            :content="allConfirmedCount"
            bgcolor="#252550"
            :loading="loadingConfirmedCount"
          />
        </v-col>
        <v-col offset="2" offset-sm="1" cols="8" md="3">
          <Card
            title="RECOVERED"
            :content="allRecoveredCount"
            bgcolor="#004D3C"
            :loading="loadingRecoveredCount"
          />
        </v-col>
        <v-col offset="2" offset-sm="1" cols="8" md="3">
          <Card
            title="DEATHS"
            :content="allDeathsCount"
            bgcolor="#7D431C"
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
    allConfirmedCount: null,
    allRecoveredCount: null,
    allDeathsCount: null
  }),
  computed: {
    loadingConfirmedCount() {
      return !this.allConfirmedCount;
    },
    loadingRecoveredCount() {
      return !this.allRecoveredCount;
    },
    loadingDeathsCount() {
      return !this.allDeathsCount;
    }
  },
  async created() {
    const { data } = await axios.get(
      "https://w3qa5ydb4l.execute-api.eu-west-1.amazonaws.com/prod/finnishCoronaData/v2"
    );
    this.allConfirmed = data.confirmed;
    this.allConfirmedCount = this.allConfirmed.length;
    this.allRecovered = data.recovered;
    this.allRecoveredCount = this.allRecovered.length;
    this.allDeaths = data.deaths;
    this.allDeathsCount = this.allDeaths.length;
  }
};
</script>
