<template>
  <v-app>
      <Navbar/>
      <NavigationDrawer/>
      <!-- <router-view/> -->
      <!-- Sizes your content based upon application components -->
      <v-main>
        <!-- Provides the application the proper gutter -->
        <v-container fluid style="background-color: #F7F7F7">
          <v-slide-y-transition>
            <!-- If using vue-router -->
            <router-view></router-view>
          </v-slide-y-transition>
        </v-container>
      </v-main>
  </v-app>
</template>
<script>
import Navbar from './components/Navbar.vue'
import NavigationDrawer from './components/NavigationDrawer.vue'
export default {
  components: {
    Navbar,
    NavigationDrawer
  }
}
</script>
<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
