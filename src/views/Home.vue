<template>
  <v-container fill-height fluid>
      <v-row align="center" justify="center">
          <v-col>
            <v-card-text class="text-xl-h4">
              This is Homepage
            </v-card-text>
            <router-link to="/dashboard">
              <v-btn>
                Visit Dashboard
              </v-btn>
            </router-link>
            <v-card-text class="text-md-body-1">
              or You can access it via Navigation Drawer (Sidebar)
            </v-card-text>
          </v-col>
      </v-row>
  </v-container>
</template>

<script>

export default {
  name: 'Home',
}
</script>
