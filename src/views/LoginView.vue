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
  <v-sheet class="mx-auto" width="300">
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
      <v-btn color="red-darken-3" class="mt-2" type="submit" block>Submit</v-btn>
    </v-form>
  </v-sheet>
</template>