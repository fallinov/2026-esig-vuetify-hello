<template>
  <h1>{{ message }}</h1>
  <input v-model="message" type="text">
  <p>Coucou GitHub ;)</p>
</template>

<script setup>
  const message = ref('Bonjour à tous !')
</script>
