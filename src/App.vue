<script setup lang="ts">
import { RouterView } from 'vue-router'
</script>

<template>
  <v-app>
    <v-app-bar>
      <v-toolbar>
        <v-app-bar-nav-icon></v-app-bar-nav-icon>        
        <v-toolbar-title>
          <v-btn to="/" variant="plain">
            Learn Vuetify 3
          </v-btn>
        </v-toolbar-title>
        <v-spacer></v-spacer>

        <v-btn icon class="mr-6">
          <v-badge color="red-darken-2" content="5">
            <v-icon icon="mdi-bell" color="blue-darken-3"></v-icon>
          </v-badge>
        </v-btn>
        
        <v-btn to="/login" variant="outlined" color="blue-darken-3" size="small">Login
        </v-btn>
      </v-toolbar>
    </v-app-bar>

    <v-main>
      <v-fade-transition>
        <v-container fluid>
          <RouterView />
        </v-container>
      </v-fade-transition>
    </v-main>
  </v-app>
</template>