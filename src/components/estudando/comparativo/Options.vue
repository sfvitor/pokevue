<script>
export default {
    data() {
        return {
            nomeAluno: 'João',
            nota1: 10,
            nota2: 10,
            rendaFamiliar: 2000,
        };
    },
    computed: {
        media() {
            return (this.nota1 + this.nota2)/2;
        },
        bolsista() {
            return this.rendaFamiliar <= 2000;
        },
    },
};
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
