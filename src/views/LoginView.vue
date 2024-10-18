<script setup lang="ts">
import { ref } from 'vue'

const form = ref({
  email: '',
  password: '',
  remember: false
})

const isLoading = ref(false)

function submit() {  
  if (form.value.email === '' || form.value.password === '') {
    return;
  }
  
  isLoading.value = true;
  setTimeout(() => {
    isLoading.value = false;
    alert(JSON.stringify(form.value));
  }, 3000);
}

const rules = {
  required: (value: any) => !!value || 'Required.',
  counter: (value: any) => value.length <= 20 || 'Max 20 characters',
  email: (value: any) => {
    const pattern = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/
    return pattern.test(value) || 'Invalid e-mail.'
  },
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
            v-model="form.email"
            :rules="[rules.required, rules.email]"        
            prepend-inner-icon="mdi-email"
            label="Email"
            ></v-text-field>
            <v-text-field
            v-model="form.password"
            type="password"
            :rules="[rules.required, rules.counter]"
            prepend-inner-icon="mdi-key"            
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