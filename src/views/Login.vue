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
                    this.$router.replace('/')
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
};
</script>

<style scoped>
    input{
        height: 2rem;
        margin: 2%;
    }
    .inputs{ 
        display: flex;
        justify-content: center;
    }
    .message{
        margin: 2%;
    }
</style>