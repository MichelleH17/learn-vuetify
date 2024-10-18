<script setup lang="ts">
import { ref } from 'vue'

const form = ref({
  email: '',
  password: '',
  remember: false
})

const isLoading = ref(false)

function submit() {
  isLoading.value = true;

  setTimeout(() => {
    isLoading.value = false;
    alert(JSON.stringify(form.value));
  }, 3000);
}
</script>

<template>
  <v-overlay :model-value="isLoading" class="align-center justify-center">
    <v-progress-circular v-if="isLoading"
      color="white"
      indeterminate
    ></v-progress-circular>
  </v-overlay>
  <v-row justify="center">
    <v-col cols="4">
      <v-card class="pa-4">
        <v-card-item>
          <v-card-title class="pb-4 text-h4 text-center">Login Form</v-card-title>
        </v-card-item>
        <v-card-text>
          <v-form @submit.prevent="submit">
            <v-text-field
            variant="solo"
            prepend-inner-icon="mdi-email"
            v-model="form.email"
            label="Email"
            ></v-text-field>
            <v-text-field
            type="password"
            variant="solo"
            prepend-inner-icon="mdi-key"
            v-model="form.password"
            label="Password"
            ></v-text-field>
            <v-checkbox
            v-model="form.remember"
            color="red-darken-3"
            label="Remember me"
            hide-details
            ></v-checkbox>            
            <v-btn variant="elevated" color="red-darken-3" class="mt-2" type="submit" size="large" block text="Submit"></v-btn>
          </v-form>
        </v-card-text>
        <v-card-actions class="d-flex flex-column">  
          <v-btn to="/register" variant="plain" class="mt-2">Register</v-btn>    
        </v-card-actions>
      </v-card>
    </v-col>
  </v-row>
</template>