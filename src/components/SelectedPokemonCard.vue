<script setup>
const props = defineProps(['pokemon', 'loading']);
</script>

<template>
  <div
    class="card card-selected-pokemon"
    :class="loading ? '' : 'animate__animated animate__flipInY'"
  >
    <img
      v-if="pokemon"
      :src="pokemon.sprites.other.dream_world.front_default"
      class="card-img-top pt-2"
      :alt="pokemon?.name"
      height="250"
    />

    <img
      v-else
      src="../assets/egg_pokemon.svg"
      class="card-img-top pt-2"
      alt="???"
      height="250"
    />

    <div class="card-body">
      <h5 class="card-title text-center">
        {{ pokemon?.name || '???' }}
      </h5>
      <hr />
      <div class="row">
        <section class="col">
          <strong>XP:</strong>
          <span>
            {{ pokemon?.base_experience }}
          </span>
        </section>
        <section class="col">
          <strong>Altura:</strong>
          <span>
            {{ pokemon?.height }}
          </span>
        </section>
      </div>
    </div>
  </div>
</template>

<style scoped>
.card-selected-pokemon {
    height: 75vh;
    background: rgb(72,63,251);
    background: radial-gradient(circle, rgba(220, 194, 106, 0.8) 0%, rgba(244, 0, 0, 0.8) 100%);
}
.card-selected-pokemon img{
    height: 250px;
}

@media (max-width: 768px) {
    .card-selected-pokemon {
        height: 30vh;
        width: 40%;
        margin: 0 auto 10px auto;
    }
    .card-selected-pokemon img{
        height: 100px;
    }
}
</style>


