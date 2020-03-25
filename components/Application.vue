<template>
  <v-container class="pb-1">
    <v-row class="text-left">
      <v-col cols="12"></v-col>
      <v-col class="mb-4">
        <h1 class="font-weight-bold mb-3 page-heading">
          CORONAVIRUS (COVID-19) STATISTICS OF FINLAND
        </h1>
      </v-col>
    </v-row>
    <total></total>
    <Table></Table>
    <Footer></Footer>
  </v-container>
</template>

<script>
import Table from "./Table";
import Total from "./Total";
import Footer from "./Footer";

export default {
  name: "Application",
  components: {
    Table,
    Total,
    Footer
  }
};
</script>
