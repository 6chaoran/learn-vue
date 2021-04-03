<template>
  <v-list rounded>
    <v-list-item-group color="indigo" v-model="selectedTab">
      <v-list-item
        v-for="(item, i) in tabs"
        :key="i"
        :to="item.to"
        @click="$emit('updateTabName', item.name)"
      >
        <v-list-item-icon>
          <v-icon v-text="item.icon"></v-icon>
        </v-list-item-icon>
        <v-list-item-content>
          <v-list-item-title v-text="item.name"></v-list-item-title>
        </v-list-item-content>
      </v-list-item>
    </v-list-item-group>
  </v-list>
</template>

<script>
export default {
  name: "SideBar",
  data() {
    return {
      tabs: [
        { name: "Home", to: "/", icon: "mdi-account" },
        { name: "About", to: "/about", icon: "mdi-flag" },
      ],
      selectedTab: 0,
    };
  },
};
</script>