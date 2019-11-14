<template>
  <v-app>
    <v-app-bar app flat color="indigo" dark>
      <v-btn v-if="isHome === false" icon @click="goBack">
        <v-icon>mdi-arrow-left</v-icon>
      </v-btn>
      <v-toolbar-title>
        <!-- <v-btn text link to="/">Lista de Compras</v-btn> -->
        <router-link style="text-decoration:none; color:white" to="/">
          Lista de Compras
        </router-link>
      </v-toolbar-title>

      <v-spacer></v-spacer>
      <v-btn icon>
        <v-icon>mdi-settings</v-icon>
      </v-btn>
    </v-app-bar>

    <v-content>
      <router-view />
    </v-content>
  </v-app>
</template>

<script>
export default {
  name: "App",

  components: {},

  data: () => ({
    isHome: null
    //
  }),
  methods: {
    goBack() {
      this.$router.go(-1);
    }
  },
  watch: {
    $route() {
      if (this.$route.path === "/") {
        this.isHome = true;
      } else {
        this.isHome = false;
      }
    }
  },
  created() {
    if (this.$route.path === "/") {
      this.isHome = true;
    }
    console.log(this.$route);
  }
};
</script>

<style>
* {
  font-family: "Poppins", sans-serif;
}

.fill-height {
  height: calc(100vh - 142px);
}
</style>
