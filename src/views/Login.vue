<template>
  <div class="login">
      <h1>Login</h1>
      <input class="input" type="text" placeholder="Email">
      <input class="input" type="password" placeholder="Senha">
      <div class="btn-login">
          <button>Login</button>
      </div>
      <p>Você não tem conta?
          <a href="/registrar">crie uma conta</a>
      </p>
  </div>
</template>

<script>
export default {
    name: 'Login',
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