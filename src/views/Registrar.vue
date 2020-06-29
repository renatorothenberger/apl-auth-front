<template>
  <div class="registra">
      <h1>Crie uma conta</h1>
    <input class="input" type="text" placeholder="Nome completo">
    <input class="input" type="text" placeholder="Email">
    <input class="input" type="password" placeholder="Senha">
    <input class="input" type="password" placeholder="Repita a senha">

    <div class="btn-cadastrar">
        <button>Cadastrar</button>
    </div>
  </div>
</template>

<script>
export default {
    name: 'Registrar',
    data() {
        return {};
    },
    methods: {}
};
</script>

<style scoped>
    .input{
        height: 2rem;
        margin: 5%;
    }
</style>