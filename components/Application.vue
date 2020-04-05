<template>
  <v-container class="pb-1">
    <v-row class="text-left">
      <v-col cols="1"
        ><img src="../static/logo.svg" alt="logo" width="40px" height="40px"
      /></v-col>
      <v-col class="mb-4">
        <h1 class="font-weight-bold mb-3 page-heading">
          CORONAVIRUS (COVID-19) STATISTICS OF FINLAND
        </h1>
      </v-col>
    </v-row>
    <total></total>
    <new-case></new-case>
    <Table></Table>
    <Footer></Footer>
  </v-container>
</template>

<script>
import Table from "./Table";
import Total from "./Total";
import Footer from "./Footer";
import NewCase from "./NewCase.vue";

export default {
  name: "Application",
  components: {
    Table,
    Total,
    Footer,
    NewCase
  }
};
</script>
