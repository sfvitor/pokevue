<script setup>
const pokemon = defineProps(['name', 'urlSvg']);

</script>

<template>
  <div class="col-4">
    <div class="card p-2 mb-3 pokemon-card">
      <p class="text-center">
        {{ pokemon.name }}
      </p>
      <img
        :src="urlSvg"
        class="card-img-top"
        alt="..."
        height="80"
      />
    </div>
  </div>
</template>

<style scoped>
.pokemon-card {
    background: rgb(72,63,251);
    background: radial-gradient(circle, rgba(94, 87, 232, 0.6) 0%, rgba(70,252,244,0.2) 100%);
    cursor: pointer;
}
.pokemon-card:hover{
    background: rgb(72,63,251);
    background: radial-gradient(circle, rgba(72,63,251,0.6) 0%, rgba(70,252,244,0.4) 100%);
}
.pokemon-card img:hover{
    padding: .1rem;
}
</style>
