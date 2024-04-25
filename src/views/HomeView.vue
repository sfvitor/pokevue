<script setup>
import { onMounted, reactive, ref, computed } from 'vue';

import PokemonCard from '../components/PokemonCard.vue';
import SelectedPokemonCard from '../components/SelectedPokemonCard.vue';

const urlBaseSvg = ref('https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/');
const pokemons = reactive(ref());
const searchPokemonField = ref('');
const selectedPokemon = reactive(ref());
const loading = ref(false);

onMounted(() => {
  fetch('https://pokeapi.co/api/v2/pokemon?limit=151&offset=0')
    .then(res => res.json())
    .then(res => pokemons.value = res.results);
});

const filteredPokemons = computed(() => {
  if (!pokemons.value || !searchPokemonField.value) {
    return pokemons.value;
  }
  return pokemons.value.filter(({ name }) => name.toLowerCase().includes(searchPokemonField.value.toLowerCase()));
});

async function selectPokemon(pokemon) {
  loading.value = true;
  await fetch(pokemon.url)
    .then(res => res.json())
    .then(res => selectedPokemon.value = res)
    .catch(err => alert(err))
    .finally(() => loading.value = false);
}

</script>

<template>
  <main>
    <div class="container text-body-secondary">
      <div class="row mt-4">
        <div class="col-sm-12 col-md-6">
          <SelectedPokemonCard
            :pokemon="selectedPokemon"
            :loading="loading"
          />
        </div>

        <div class="col-sm-12 col-md-6">
          <div class="card card-pokemon-list">
            <div class="card-body row">

              <div class="mb-3">
                <label
                  hidden
                  for="search-pokemon-field"
                  class="form-label"
                >
                  Pesquisar...
                </label>
                <input
                  v-model="searchPokemonField"
                  type="text"
                  class="form-control"
                  id="search-pokemon-field"
                  placeholder="Pesquisar..."
                />
              </div>

              <PokemonCard
                v-for="pokemon in filteredPokemons"
                :key="pokemon.name"
                :name="pokemon.name"
                :urlSvg="urlBaseSvg + pokemon.url.split('/')[6] + '.svg'"
                @click="selectPokemon(pokemon)"
              />
            </div>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<style scoped>
.card-pokemon-list {
  max-height: 75vh;
  overflow-y: scroll;
  overflow-x: hidden;
}
</style>
