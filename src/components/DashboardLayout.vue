<template>
  <div class="dashboard">
    <!-- Buat Navbar -->
    <v-app-bar color="grey darken-4" dark app>
      <v-app-bar-nav-icon @click="drawer = true"></v-app-bar-nav-icon>

      <v-toolbar-title>Guided Vuefire</v-toolbar-title>
      <v-spacer></v-spacer>

      <v-btn icon @click="logout"><v-icon>mdi-logout</v-icon></v-btn>

    </v-app-bar>
    <!-- -->

    <!-- Buat Sidebar -->
    <v-navigation-drawer v-model="drawer" absolute temporary>
      <!-- Cashier Icon dan nama -->
      <v-list-item>
        <v-list-item-content>
          <v-icon size="70" class="mb-5">$cashier</v-icon>
          <v-list-item-title class="text-h4 font-weight-medium mb-10">
            Cashier
          </v-list-item-title>
        </v-list-item-content>
      </v-list-item>

      <v-divider></v-divider>

      <v-list dense nav>
        <v-list-item
          v-for="item in items"
          :key="item.title"
          link
          tag="router-link"
          :to="item.to"
        >
          <v-list-item-content>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <!--  -->

    <div class="grey lighten-4 fullheight pa-5">
      <router-view></router-view>
    </div>
  </div>
</template>

<script>
import { mdiAccount } from "@mdi/js";

export default {
  name: "Dashboard",
  data: () => ({
    drawer: false,
    group: null,
    svgPath: mdiAccount,
    items: [
      { title: "Dashboard", to: "/" },
      { title: "Item List", to: "/gd" },
      { title: "Order", to: "/order" },
      { title: "Transaction History", to: "/history" },
      { title: "Make Promo", to: "/tgs" },
    ],
  }),

  computed: {
    platform() {
      return "$" + this.user.platform;
    },
  },
};
</script>

<style scoped>
.fullheight {
  min-height: 100vh !important;
}
</style>