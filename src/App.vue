<script setup>
  // import { computed, ref } from 'vue'
  const newPokemon = ref('Charizard')
  const inputNewPokemon = useTemplateRef('inputNewPokemon') // Champ de saisie
  const showElectricOnly = ref(false)
  const pokemons = ref([
    { name: 'Pikachu', type: 'Electric' },
    { name: 'Bulbasaur', type: 'Grass' },
    { name: 'Charmander', type: 'Fire' },
    { name: 'Squirtle', type: 'Water' },
    { name: 'Jolteon', type: 'Electric' },
  ])

  // TODO: ref pour le filtre
  // TODO: computed filteredPokemons
  function addPokemon () {
    // Ajoute un pokémon à la fin du tableau
    pokemons.value.push({ name: newPokemon.value, type: 'Electric' })
    // On vide le champ
    newPokemon.value = ''
    // Remet le focus au champ
    inputNewPokemon.value.focus()
  }

  // Computed qui filtre les pokémons
  const filterdPokemons = computed(() => {
    if (showElectricOnly.value) {
      return pokemons.value.filter(p => p.type === 'Electric')
    }
    return pokemons.value
  })
</script>

<template>
  <main>
    <h1>Mon Pokédex sur Vercel de test</h1>
    <p>{{ newPokemon }}</p>
    <div>
      <input ref="inputNewPokemon" v-model="newPokemon" type="text" @keyup.enter="addPokemon">
      <button @click="addPokemon">Ajouter</button>
    </div>
    <!-- TODO: checkbox filtre -->
    <h2>Mes pokémons</h2>
    <div>
      <label>
        <input v-model="showElectricOnly" type="checkbox">
        Afficher uniquement les "Electric"
      </label>
    </div>
    <p v-if="filterdPokemons.length === 0">Aucun pokémon attrapé !</p>
    <ul v-else>
      <li v-for="p in filterdPokemons" :key="p.name">
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
