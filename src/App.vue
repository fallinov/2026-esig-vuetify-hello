<script setup>
  // import { computed, ref } from 'vue'
  const newPokemon = ref('Charizard')
  const pokemons = ref([
    { name: 'Pikachu', type: 'Electric' },
    { name: 'Bulbasaur', type: 'Grass' },
    { name: 'Charmander', type: 'Fire' },
    { name: 'Squirtle', type: 'Water' },
    { name: 'Jolteon', type: 'Electric' },
  ])

  // TODO: ref pour le nom
  // TODO: ref pour le filtre
  // TODO: computed filteredPokemons
  // TODO: function addPokemon()
  function addPokemon () {
    alert('Coucou !')
  }
</script>

<template>
  <main>
    <h1>Mon Pokédex</h1>
    <p>{{ newPokemon }}</p>
    <!-- TODO: input + button -->
    <div>
      <input v-model="newPokemon" type="text">
      <button @click="addPokemon">Ajouter</button>
    </div>
    <!-- TODO: checkbox filtre -->
    <!-- TODO: v-for liste -->
    <h2>Mes pokémons</h2>
    <p v-if="pokemons.length === 0">Aucun pokémon attrapé !</p>
    <ul v-else>
      <li v-for="p in pokemons" :key="p.name">
        {{ p.name }}
        ({{ p.type }})
      </li>
    </ul>

  </main>
</template>

<style scoped>
  main {
    padding: 20px;
  }

  h1 {
    color: orange;
  }

  input {
    border: 2px solid orange;
    padding: 5px;
  }

  button {
    border: 2px solid orange;
    padding: 5px;
    margin:  0 1em;
  }
</style>
