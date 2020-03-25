<template>
  <v-app>
    <v-content>
      <Application />
    </v-content>
  </v-app>
</template>

<script>
import Application from "../components/Application";
export default {
  name: "App",
  components: {
    Application
  },

  data: () => ({
    //
  })
};
</script>

<style>
.page-heading {
  color: #252550;
  font-size: 2.125rem;
  line-height: 2.5rem;
  letter-spacing: 0.00735em !important;
  font-family: "Sen", "sans-serif";
}
.page-title {
  color: #252550;
  font-size: 1.5rem;
  line-height: 2rem;
  letter-spacing: 0.00735em !important;
  font-family: "Sen", "sans-serif";
}
</style>
