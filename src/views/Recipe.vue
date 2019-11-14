<template>
  <v-card class="fill-height" flat style="borderRadius:0">
    <v-toolbar dark flat color="indigo">
      <v-toolbar-title class="subtitle-1 mx-auto">Nueva Receta</v-toolbar-title>
    </v-toolbar>
    <v-card-text style="height: 100%">
      <v-card class="mx-auto mb-4">
        <v-card-title class="subtitle-1">Receta #1</v-card-title>
      </v-card>
      <v-card class="mx-auto mb-4">
        <v-card-title class="subtitle-1">Receta #2</v-card-title>
      </v-card>
      <v-card class="mx-auto">
        <v-card-title class="subtitle-1">Receta #3</v-card-title>
      </v-card>
    </v-card-text>
    <v-fab-transition>
      <v-btn
        v-if="fab"
        color="success"
        fab
        large
        dark
        bottom
        right
        class="v-btn--example"
      >
        <v-icon>mdi-plus</v-icon>
      </v-btn>
    </v-fab-transition>
  </v-card>
</template>

<script>
export default {
  data: () => ({
    fab: false
  }),
  mounted() {
    this.fab = true;
  }
};
</script>
