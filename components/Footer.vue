<template>
  <v-footer light padless>
    <div id="footer">
      <p class="text-center white--text font-weight-light pa-2">
        Made by
        <b>Sagar Acharya</b>
        <a href="https://twitter.com/acharyasaagar" target="_blank">
          <v-btn class="ml-4 white--text" icon>
            <v-icon size="24px">mdi-twitter</v-icon>
          </v-btn>
        </a>
        <a href="https://www.linkedin.com/in/acharyasaagar/" target="_blank">
          <v-btn class="mx-4 white--text" icon>
            <v-icon size="24px">mdi-linkedin</v-icon>
          </v-btn>
        </a>
      </p>
      <v-divider dark></v-divider>
      <p class="white--text text-center font-weight-light mt-3 pa-2">
        Data Source: Helsingin Sanomat
        <a
          href="https://github.com/HS-Datadesk/koronavirus-avoindata"
          target="_blank"
          >(Github Repo here)</a
        >
      </p>
      <p class="white--text text-center font-weight-light mb-3">
        Data Source: Covid19 Api
        <a href="https://covid19api.com/" target="_blank">(covid19api)</a>
      </p>
      <v-divider dark></v-divider>
      <p class="headline pa-2 text-center white--text mt-4">DISCLAIMER:</p>
      <p class="white--text text-center font-weight-light ">
        I do not guarantee the information in this website is complete or
        accurate or up-to-date. You are using this site at your own risk and I
        will not be liable for any losses or damages caused due to the use of
        this website.
      </p>
    </div>
  </v-footer>
</template>

<script>
export default {
  name: "Footer"
};
</script>

<style scoped>
a {
  text-decoration: none;
}
#footer {
  background: #252550;
  min-width: 100%;
  padding: 25px;
}
</style>
