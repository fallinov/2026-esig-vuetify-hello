<template>
  <h1>{{ message }}</h1>
  <input v-model="message" type="text">
  <p>Coucou 55</p>
</template>

<script setup>
  const message = ref('Bonjour à tous !')
</script>
