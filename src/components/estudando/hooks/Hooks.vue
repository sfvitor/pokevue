<script setup>
import { ref, onMounted, computed, reactive } from 'vue';
const nome = ref('Vue');
onMounted(() => {
    nome.value = 'Vite';
});
const temperatura = ref(22);
const temperaturaVerificada = computed(() => {
    return `Temperatura ${temperatura.value > 21 ? 'alta' : 'baixa'}`;
});
function verificaTemperatura() {
    return `Temperatura ${temperatura.value > 21 ? 'alta' : 'baixa'}`;
}

const pessoa = reactive({
    nome: 'Joe',
    idade: 30,
});

onMounted(() => {
    pessoa.nome = 'João';
    console.log(pessoa);
});
</script>

<template>
    <div class="col-6">
        <h2>Hooks</h2>
        <p>{{nome}}</p>
        <input
            type="text"
            v-model="nome"
        />
        <hr />
        <span>Computed: {{temperaturaVerificada}}</span> <br />
        <span>Function: {{verificaTemperatura()}}</span> <br />
        <input
            type="number"
            v-model="temperatura"
        />
        <hr />
        <p>{{pessoa.nome}}</p>
        <p>{{pessoa.idade}}</p>
    </div>
</template>

<style scoped>

</style>
