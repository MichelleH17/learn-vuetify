<script setup lang="ts">
import { ref } from 'vue'
import { RouterView } from 'vue-router'
import { useTheme } from 'vuetify';

const notifications = ref([
  { 
    title: 'Message from A',
    icon: 'mdi-email',
    color: 'red'
  },
  { 
    title: 'Message from B',
    icon: 'mdi-email',
    color: 'gray'
  },
  { 
    title: 'Message from C',
    icon: 'mdi-email',
    color: 'blue' 
  },
  { 
    title: 'Message from D',
    icon: 'mdi-email',
    color: 'green'
  },
  { 
    title: 'Message from E',
    icon: 'mdi-email',
    color: 'yellow'
  }
])

const darkTheme = ref(true)
const theme = useTheme()

function changeTheme() {
  darkTheme.value = !darkTheme.value
  theme.global.name.value = darkTheme.value ? 'dark' : 'light'
}

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

        <v-btn class="mr-2" icon @click="changeTheme">
          <v-icon :icon="darkTheme ? 'mdi-weather-night' : 'mdi-weather-sunny'" size="large"></v-icon>
        </v-btn>
        
        <v-menu open-on-hover transition="scale-transition">
          <template v-slot:activator="{ props }">
            <v-btn v-bind="props" icon class="mr-4">
              <v-badge color="red-darken-2" content="5">
            <v-icon icon="mdi-bell" color="blue-darken-3" size="large"></v-icon>
          </v-badge>
        </v-btn>
          </template>
          <v-list>
            <v-list-item
              v-for="(item, index) in notifications"
              :key="index"
              :value="index"
              class="justify-center"
            >
              <v-list-item-title>
                <v-icon :color="item.color" :icon="item.icon"></v-icon>
                {{ item.title }}</v-list-item-title>
            </v-list-item>
          </v-list>
        </v-menu>
        
        <v-btn to="/login" variant="outlined" size="small">Login
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