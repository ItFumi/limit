<template>
  <v-app>
    <!-- ヘッダー -->
    <v-app-bar color="black white--text" app clipped-right>
      <v-toolbar-title class="text-h5 font-weight-bold">
        <router-link :to="{name: 'Home'}" class="logo">Limit</router-link>
      </v-toolbar-title>
      <v-list>
        <v-list-item v-for="nav_list in nav_lists" :key="nav_list.name" @click="autoQuizScroll(nav_list.link)">
          <router-link class="nav-link" :to="nav_list.link">
            <v-list-item-icon>
              <v-icon>{{ nav_list.icon }}</v-icon>
            </v-list-item-icon>
            <v-list-item-content>
              <v-list-item-title class="text-center">{{ nav_list.name }}</v-list-item-title>
            </v-list-item-content>
          </router-link>
        </v-list-item>
      </v-list>
    </v-app-bar>
    <v-main class="main">
      <router-view />
    </v-main>
  </v-app>
</template>
<script>
export default {
  data() {
    return{
      drawer: false,
      nav_lists:[
        {name: 'クイズを作る',icon: 'mdi-lead-pencil',link: '/Make'},
        {name: 'クイズに答える',icon: 'mdi-hand-back-right-outline',link: '/Answer'}
      ]
    }
  }
};
</script>
<style lang="scss">
  .v-application a {
    color: transparent;
    text-decoration: none;
  }
  .v-application p {
    margin-bottom: 0;
  }
  .v-application .v-toolbar__content {
    justify-content: space-between;
  }
  .v-application .v-list-item__icon {
    margin-right: 10px !important;
  }
  #app {
    color: #2c3e50;
    font-family: "游ゴシック Medium", "游ゴシック体", "Yu Gothic Medium", YuGothic, "ヒラギノ角ゴ ProN", "Hiragino Kaku Gothic ProN", "メイリオ", Meiryo, "ＭＳ Ｐゴシック", "MS PGothic", sans-serif;
    text-align: center;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
  }
  #app .logo {
    color: #fff;
    text-decoration: none;
  }
  #app .v-list {
    background: transparent;
    display: flex;
  }
  #app .v-list .v-list-item {
    padding: 0;
  }
  #app .v-list .v-list-item .nav-link {
    align-items: center;
    background-color: #3A3F40;
    border-radius: 3px;
    display: flex;
    flex: 1 1 100%;
    min-height: 48px;
    margin-left: 10px;
    min-height: auto;
    min-width: 140px;
    padding: 0;
    position: relative;
    transition: all .2s ease-out;
  }
  #app .v-list .v-list-item .nav-link .v-list-item__icon {
    align-self: center;
    margin: 0 0 0 10px !important;
  }
  #app .v-list .v-list-item .nav-link .v-list-item__title {
    color: #FFF;
    font-size: 12px;
  }
  #app .v-list .v-list-item .nav-link:hover {
    opacity: .6;
  }
  #app .v-list .v-list-item .nav-link .v-list-item__icon .v-icon {
    color: #FFF;
  }
</style>