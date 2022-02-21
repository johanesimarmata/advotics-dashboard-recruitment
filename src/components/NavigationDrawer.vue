<template>
     <v-navigation-drawer
          app
          v-model="drawer"
          :mini-variant.sync="mini"
          permanent
          style="min-height: 100vh; min-width: 60px; margin-top: 70px;"
    >
          <v-list-item class="px-2">
               <v-list-item-avatar>
                    <v-icon v-if="mini" style="color: #C5C5C5;">mdi-menu</v-icon>
               </v-list-item-avatar>

               <v-list-item-title>Menu</v-list-item-title>
               <v-btn
                    icon
                    @click.stop="mini = !mini"
               >
                    <v-icon style="color: #C5C5C5;">mdi-menu-open</v-icon>
               </v-btn>
          </v-list-item>

      <v-divider></v-divider>

      <v-list dense>
        <v-list-item
          to="/"
          link
        >
          <v-list-item-icon class="itemIcon">
                <v-img src="../assets/images/Home Icon.png"></v-img>
          </v-list-item-icon>

          <v-list-item-content>
            <v-list-item-title>Home</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
        <v-list-item
          to="/dashboard"
          link
        >
          <v-list-item-icon class="itemIcon">
                <v-img src="../assets/images/Dashboard icon.png"></v-img>
          </v-list-item-icon>

          <v-list-item-content>
            <v-list-item-title>Dashboard</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
</template>

<script>
export default {
     name: 'NavigationDrawer',
     data() {
          return {
               drawer: true,
               items: [
                    { title: 'Home', route: '/', icon: '../assets/images/Home Icon.png'},
                    { title: 'Dashboard', route: '/dashboard', icon: '../assets/images/Dashboard icon.png' },
               ],
               mini: true,
          }
     },
}
</script>

<style scoped>
     a{
          padding: 14px 24px;
     }
</style>