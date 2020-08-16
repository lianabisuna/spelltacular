<template>
  <v-app>
    <v-app-bar app color="primary" dark>
      <v-toolbar-title class="font-weight-black">Spelltacular</v-toolbar-title>

      <v-spacer></v-spacer>

      <v-btn
        icon
      >
        <v-icon>mdi-home</v-icon>
      </v-btn>
    </v-app-bar>

    <v-main>
      <router-view></router-view>
    </v-main>
  </v-app>
</template>

<script>
// import HelloWorld from "./components/HelloWorld";

export default {
  name: "App",

  components: {
    // HelloWorld
  },

  data: () => ({
    //
  })
};
</script>
