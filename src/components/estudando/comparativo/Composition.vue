<script setup>
import { computed, ref } from 'vue';
const nomeAluno = ref('João');
const nota1 = ref(10);
const nota2 = ref(10);
const media = computed(() => (nota1.value + nota2.value)/2);
const rendaFamiliar = ref(2000);
const bolsista = computed(() => rendaFamiliar.value <= 2000);
</script>

<template>
    <div class="col-6">
        <h2>Composition</h2>
        <h3>{{nomeAluno}}</h3>
        <input
            type="number"
            v-model="nota1"
        />
        <input
            type="number"
            v-model="nota2"
        />
        <p>Média: {{ media }}</p>
        <hr />
        <input
            type="number"
            v-model="rendaFamiliar"
        />
        <button
            class="btn mt-3"
            :class="bolsista ? 'btn-success' : 'btn-danger'"
        >
            {{bolsista}}
        </button>
    </div>
</template>

<style scoped>
    .btn-success {
        background-color: hsl(120, 50%, 50%);
    }
    .btn-danger {
        background-color: hsl(0, 50%, 50%);
    }
</style>
