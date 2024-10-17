<script setup>
import { ref } from 'vue'

const form = ref({
  email: '',
  password: '',
  remember: false
})

function submit() {
  console.log(form.value)
  alert(JSON.stringify(form.value))
}
</script>

<template>
  <v-card class="pa-6 mx-auto" width="400">
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
      </v-form>
    </v-card-text>
    <v-card-actions class="d-flex flex-column">
      <v-btn  variant="elevated" color="red-darken-3" class="mt-2" type="submit" block>Submit</v-btn>
      <v-btn to="/register" variant="plain" class="mt-2">Register</v-btn>    
    </v-card-actions>
  </v-card>
</template>