<template>
  <v-app>
    <v-app-bar app flat color="indigo" dark>
      <v-toolbar-title>Lista de Compras</v-toolbar-title>

      <v-spacer></v-spacer>
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
    //
  })
};
</script>
