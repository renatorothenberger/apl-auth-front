<template>
  <div class="login">
      <h1>Login</h1>
      <div class=inputs>
        <input class="input" type="text" placeholder="Email" v-model="email">
        <input class="input" type="password" placeholder="Senha" v-model="password">
      </div>
      <div class="message">{{ info }}</div>
      <div class="btn-login">
          <button @click="login">Login</button>
      </div>
      <p>Você não tem conta?
          <router-link to="/registrar"> crie uma conta</router-link>
      </p>
  </div>
</template>

<script>
import axios from 'axios';

export default {
    name: 'Login',
    data() {
        return {
            info: ''
        };
    },
    methods: {
        login() {
            if(!this.email || !this.password){
                this.info = 'Preencha o e-mail e a senha'
            } else {
                return axios.get('http://localhost:8000/api/auth', {
                    params: {
                        email: this.email,
                        password:  this.password
                    }
                },{
                    headers: {
                        'Content-type': 'application/json',
                    }
                }).then((response) => {
                    if (response.data.token) {
                        sessionStorage.setItem('userName', response.data.name)
                        this.$router.replace('/home')
                    } else {
                        this.info = response.data
                    }
                }).catch(error => {
                    console.log({
                        error: error
                    });
                });
            }
        }
    }
};
</script>

<style scoped>
    input{
        height: 2rem;
        margin: 2%;
    }
    .inputs{ 
        align-items: center;
        display: flex;
        flex-direction: column;
        margin-left: 25%;
        width: 50%;
    }
    .message{
        margin: 2%;
    }
</style>