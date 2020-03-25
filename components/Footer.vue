<template>
  <v-footer light padless="">
    <v-card flat tile color="#252550" class="mx-auto mt-5 pb-3">
      <v-card-text class="text-center white--text font-weight-light">
        Made by <b>Sagar Acharya </b>
        <a href="https://twitter.com/acharyasaagar">
          <v-btn class="mx-4 white--text" icon>
            <v-icon size="24px">mdi-twitter</v-icon>
          </v-btn>
        </a>
        <a href="https://www.linkedin.com/in/acharyasaagar/">
          <v-btn class="mx-4 white--text" icon>
            <v-icon size="24px">mdi-linkedin</v-icon>
          </v-btn>
        </a>
      </v-card-text>
      <v-divider></v-divider>
      <v-card-text class="headline pa-2 text-center white--text"
        >DISCLAIMER:
      </v-card-text>
      <v-card-text class="white--text text-center font-weight-light">
        I do not guarantee the information in this website is complete or
        accurate or up-to-date. You are using this site at your own risk and I
        will not be liable for any losses or damages caused due to the use of
        this website.
      </v-card-text>
    </v-card>
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
</style>
