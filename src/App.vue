<template>
  <v-form ref="form">
    <v-app>
      <v-app-bar color="blue" dark fixed app>
        <router-link style="text-decoration: none;" to="/">
          <v-btn text>
            <span class="mr-2"><h1>Dinks Store</h1></span>
            <v-icon>mdi-store</v-icon>
          </v-btn>
        </router-link>

        <v-spacer />

        <v-btn text href="/">
          <span class="mr-2"><span class="mr-2">RESET</span></span>
          <v-icon>mdi-refresh</v-icon>
        </v-btn>
      </v-app-bar>

      <v-main>
        <router-view />
      </v-main>

      <v-footer color="blue" dark rounded>
        <v-col class="text-center" cols="12">
          <span class="mr-2">Date</span>
          {{ new Date().getFullYear() }} / {{ new Date().getMonth() + 1 }} /
          {{ new Date().getDate() }}
        </v-col>
        <v-col class="text-center" cols="12">
          <span class="mr-2"
            ><strong>
              Made by
              <a
                href="https://www.facebook.com/arm.jaruwat.35/"
                style="color: white; text-decoration: none;"
              >
                Jaruwat Taengnuan
              </a>
            </strong></span
          >
          <v-icon>mdi-account</v-icon>
        </v-col>
      </v-footer>
    </v-app>
  </v-form>
</template>

<script>
export default {
  name: "App",

  components: {},

  data: () => ({})
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  padding: 30px;
}
</style>
