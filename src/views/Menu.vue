<template>
  <v-card class="fill-height" flat style="borderRadius:0">
    <v-toolbar dark flat color="indigo">
      <v-toolbar-title class="subtitle-1 mx-auto">
        <span v-if="show.menuTitle" @click="toggleMenuTitle">{{
          menu.title
        }}</span>
        <!-- <v-col cols="12" sm="6" md="3"> -->
        <v-text-field
          v-else
          autofocus
          @change="toggleMenuTitle"
          label="Nuovo Menu"
          v-model="menu.title"
        ></v-text-field>
        <!-- </v-col> -->
      </v-toolbar-title>
    </v-toolbar>
    <v-card-text style="height: 100%">
      <v-card class="mx-auto mb-4">
        <v-card-title class="subtitle-1">Lunes</v-card-title>
      </v-card>
      <v-card class="mx-auto mb-4">
        <v-card-title class="subtitle-1">Martes</v-card-title>
      </v-card>
      <v-card class="mx-auto">
        <v-card-title class="subtitle-1">Miercoles</v-card-title>
      </v-card>
    </v-card-text>
    <v-fab-transition>
      <v-btn
        v-if="fab"
        tag="router-link"
        :to="{ name: 'create-recipe' }"
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
    fab: false,
    show: {
      fab: false,
      menuTitle: true
    },
    menu: {
      title: "Nuevo Menu"
    }
  }),
  methods: {
    toggleMenuTitle() {
      this.show.menuTitle = !this.show.menuTitle;
    }
  },
  mounted() {
    this.fab = true;
  }
};
</script>
