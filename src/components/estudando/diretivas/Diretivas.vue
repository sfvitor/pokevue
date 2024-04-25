<script setup>
import { ref, onMounted, computed, reactive } from 'vue';

// v-model
const nome = ref('Fulano');

// v-if e v-else e v-else-if
const exibir = false;
// se Falsy, nem renderiza
// v-show renderiza, mas se for Falsy, deixa com display: none no css

// v-for
const pessoas = [
    {
        nome: 'João',
        id: 1,
    },
    {
        nome: 'Maria',
        id: 2,
    },
];

</script>

<template>
    <div class="col-6">
        <h2>Diretivas</h2>

        <h3>v-model</h3>
        <span>{{nome}}</span> <br />
        <input type="text" v-model="nome" />

        <h3>v-if e v-else e v-else-if</h3>
        <span v-if="exibir">Olá, pessoas!</span>
        <span v-else-if="exibir === null">É nulooo!</span>
        <span v-else>Oh nooo!</span>

        <h3>v-show</h3>
        <span v-show="exibir">agora é com o v-show</span>

        <h3>v-for</h3>
        <ul>
            <li
                v-for="pessoa in pessoas"
                :key="pessoa.id"
            >
                {{pessoa.nome}}
            </li>
        </ul>
    </div>
</template>

<style scoped>

</style>
