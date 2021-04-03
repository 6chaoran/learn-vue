<template>
  <div id="app">
    <v-app>
      <v-app-bar dense app dark color="indigo">
        <v-app-bar-nav-icon @click="sidebar = !sidebar"></v-app-bar-nav-icon>
        <v-app-bar-title>v-app-bar-title</v-app-bar-title>
        <v-spacer></v-spacer>
        <v-app-bar-title>{{ currentTabName }}</v-app-bar-title>
      </v-app-bar>
      <v-main>
        <!-- side bar -->
        <v-navigation-drawer absolute v-model="sidebar">
          <side-bar @updateTabName="setTabName" />
        </v-navigation-drawer>
        <!-- content -->
        <div :class="{ 'shift-right': sidebar }">
          <v-container> <router-view /></v-container>
        </div>
      </v-main>
    </v-app>
  </div>
</template>

<script>
import SideBar from "./components/SideBar.vue";
export default {
  components: { SideBar },
  data() {
    return {
      sidebar: true,
      currentTabName: "Home",
    };
  },
  methods: {
    setTabName: function (tabname) {
      this.currentTabName = tabname;
    },
  },
};
</script>

<style>
.shift-right {
  margin-left: 256px;
}
</style>
