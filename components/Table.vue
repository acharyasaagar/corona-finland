<template>
  <v-container class="pa-0 mb-5">
    <v-col class="mb-3 pa-0" cols="12">
      <h2 class="page-title font-weight-bold">CASES BY HEALTH DISTRICT:</h2>
    </v-col>
    <v-col v-if="loading" class="ma-5 pa-5" cols="12">
      <v-row justify="center" class="ma-5 pa-5">
        <v-progress-circular
          :size="80"
          :width="5"
          color="#252550"
          indeterminate
        ></v-progress-circular>
      </v-row>
    </v-col>
    <v-data-iterator
      v-if="items.length"
      :items="items"
      :items-per-page.sync="itemsPerPage"
      :page="page"
      :search="search"
      :sort-by="sortBy.toLowerCase()"
      :sort-desc="sortDesc"
      hide-default-footer
    >
      <template v-slot:header>
        <v-toolbar dark color="#252550" class="mb-1">
          <v-text-field
            v-model="search"
            clearable
            flat
            solo-inverted
            hide-details
            label="Search"
          ></v-text-field>
          <template v-if="$vuetify.breakpoint.mdAndUp">
            <v-spacer></v-spacer>
            <v-btn-toggle v-model="sortDesc" mandatory>
              <v-btn large depressed color="#252550" :value="false">
                <v-icon>mdi-arrow-up</v-icon>
              </v-btn>
              <v-btn large depressed color="#252550" :value="true">
                <v-icon>mdi-arrow-down</v-icon>
              </v-btn>
            </v-btn-toggle>
          </template>
        </v-toolbar>
      </template>
      <template v-slot:default="props">
        <v-row>
          <v-col
            v-for="item in props.items"
            :key="item.healthDistrict"
            cols="12"
            sm="6"
            md="4"
            lg="3"
          >
            <v-card>
              <v-card-title class="sub-heading font-weight-bold">
                {{ item.healthCareDistrict }}
              </v-card-title>

              <v-divider></v-divider>

              <v-list dense>
                <v-list-item v-for="(key, index) in keys" :key="index">
                  <v-list-item-content class="text-primary"
                    >{{ key }}:</v-list-item-content
                  >
                  <v-list-item-content
                    class="align-end text-primary font-weight-bold"
                    >{{ item[key.toLowerCase()] }}</v-list-item-content
                  >
                </v-list-item>
              </v-list>
            </v-card>
          </v-col>
        </v-row>
      </template>
      <template v-slot:footer>
        <v-row class="mt-2" align="center" justify="center">
          <v-spacer></v-spacer>
          <span class="mr-4 grey--text"
            >Page {{ page }} of {{ numberOfPages }}</span
          >
          <v-btn fab dark color="#252550" class="mr-1" @click="formerPage">
            <v-icon>mdi-chevron-left</v-icon>
          </v-btn>
          <v-btn fab dark color="#252550" class="mr-1" @click="nextPage">
            <v-icon>mdi-chevron-right</v-icon>
          </v-btn>
        </v-row>
      </template>
    </v-data-iterator>
  </v-container>
</template>

<script>
import axios from "axios";
export default {
  name: "Table",
  data() {
    return {
      search: "",
      sortDesc: true,
      page: 1,
      itemsPerPage: 8,
      sortBy: "confirmed",
      keys: ["Confirmed", "Recovered", "Deaths"],
      items: [],
      loading: true
    };
  },
  computed: {
    numberOfPages() {
      return Math.ceil(this.items.length / this.itemsPerPage);
    }
  },
  async created() {
    const { data } = await axios.get(
      "https://w3qa5ydb4l.execute-api.eu-west-1.amazonaws.com/prod/finnishCoronaData"
    );
    const allDistricts = [
      ...new Set(data.confirmed.map(d => d.healthCareDistrict))
    ];
    const items = allDistricts.map(district => {
      const filter = d => d.healthCareDistrict === district;
      const confirmed = data.confirmed.filter(filter);
      const recovered = data.recovered.filter(filter);
      const deaths = data.deaths.filter(filter);
      return {
        healthCareDistrict: district || "Others",
        confirmed: confirmed.length,
        recovered: recovered.length,
        deaths: deaths.length
      };
    });
    this.items = items;
    this.loading = false;
  },
  methods: {
    nextPage() {
      if (this.page + 1 <= this.numberOfPages) this.page += 1;
    },
    formerPage() {
      if (this.page - 1 >= 1) this.page -= 1;
    }
  }
};
</script>

<style>
.sub-heading,
.text-primary {
  font-family: "Sen" "Roboto" "sans-serif";
  color: #252550;
}
</style>
