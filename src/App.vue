<template>
  <v-app>
    <v-app-bar color="black white--text" app clipped-right>
      <v-toolbar-title class="text-h5 font-weight-bold">Limit</v-toolbar-title>
      <v-spacer></v-spacer>
      <v-app-bar-nav-icon color="white"></v-app-bar-nav-icon>
    </v-app-bar>
  </v-app>
</template>
<script>
export default {
  data() {
    return{
    }
  }
};
</script>
<style lang="scss">
  #app {
    color: #2c3e50;
    font-family: Avenir, Helvetica, Arial, sans-serif;
    text-align: center;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
  }
  #app .v-navigation-drawer {
    background: #3A3F40;
  }
  #app .v-list .v-icon {
    color: #FFFFFF;
  }
  #app .v-list .v-list-item__title {
    color: #FFFFFF;
  }
  #app main {
    background: linear-gradient(#540000, #BE0F21);
  }
  </style>