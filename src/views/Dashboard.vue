<template>
  <v-card flat id="lateral">
    <v-toolbar dark tabs flat color="indigo">
      <v-tabs v-model="currentTab" centered background-color="transparent">
        <v-tab href="#menu">Menus</v-tab>
        <v-tab href="#list">Listas</v-tab>
        <v-tabs-slider color="white"></v-tabs-slider>
      </v-tabs>
    </v-toolbar>
    <v-card-text v-if="isLoad" style="height: 100%">
      <v-tabs-items v-model="currentTab">
        <v-tab-item
          v-for="content in ['menu', 'list']"
          class="tab-item-wrapper"
          :value="content"
          :key="content"
        >
          <template v-if="currentTab === 'menu'">
            <v-card
              class="mx-auto mb-4"
              tag="router-link"
              v-for="{ id, title } in menuList"
              :to="{ name: 'view-menu', params: { id } }"
              :key="id"
            >
              <v-card-title class="subtitle-1">{{ title }}</v-card-title>
            </v-card>
          </template>
          <template v-else>
            <v-card class="mx-auto mb-4">
              <v-card-title class="subtitle-1">Lista #1</v-card-title>
            </v-card>
            <v-card class="mx-auto mb-4">
              <v-card-title class="subtitle-1">Lista #2</v-card-title>
            </v-card>
            <v-card class="mx-auto mb-4">
              <v-card-title class="subtitle-1">Lista #3</v-card-title>
            </v-card>
          </template>
        </v-tab-item>
      </v-tabs-items>
    </v-card-text>
    <v-fab-transition>
      <v-btn
        tag="router-link"
        :to="{ name: activeFab.action }"
        :key="activeFab.name"
        :color="activeFab.color"
        fab
        large
        dark
        bottom
        right
        class="v-btn--example"
      >
        <v-icon>{{ activeFab.icon }}</v-icon>
      </v-btn>
    </v-fab-transition>
  </v-card>
</template>

<script>
export default {
  data: () => ({
    fab: false,
    isLoad: false,
    hidden: false,
    tabs: null,
    currentTab: null,
    menuList: [],
    lists: []
  }),

  computed: {
    activeFab() {
      switch (this.currentTab) {
        case "menu":
          return {
            color: "success",
            icon: "mdi-plus",
            name: "menu",
            action: "create-menu"
          };
        case "list":
          return {
            color: "success",
            icon: "mdi-plus",
            name: "list",
            action: "create-list"
          };
        default:
          return {};
      }
    }
  },
  async created() {
    setTimeout(() => {
      this.menuList = [
        {
          id: 0,
          title: "Menu Semanal"
        }
      ];
    }, 3000);
  }
};
</script>

<style>
/* This is for documentation purposes and will not be needed in your application */
.v-btn--example {
  right: 0;
  bottom: 0;
  position: absolute;
  margin: 0 1rem 1rem 0;
}

#lateral {
  border-radius: 0;
}

.tab-item-wrapper {
  height: calc(100vh - 142px);
}
</style>
