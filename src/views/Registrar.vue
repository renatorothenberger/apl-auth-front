<template>
  <div class="registra">
      <h1>Crie uma conta</h1>
      <div class='inputs'>
        <input class="input" type="text" placeholder="Nome completo" v-model="name">
        <input class="input" type="text" placeholder="Email" v-model="email">
        <input class="input" type="password" placeholder="Senha" v-model="password">
        <input class="input" type="password" placeholder="Repita a senha" v-model="checkPassword">
      </div>

    <div class="message">{{ info }}</div>

    <div class="btn-cadastrar">
        <button @click="registrar()">Registrar</button>
    </div>
    <p>
        ou retorne ao
        <router-link to="/login"> login</router-link>
    </p>

  </div>
</template>

<script>
import axios from 'axios';

export default {
    name: 'Registrar',
    data() {
        return {
            info: ''
        };
    },
    methods: {
        registrar() {
            if (this.password != this.checkPassword) {
                this.info = 'As senhas digitadas não coincidem'
            } else if (!this.name || !this.email || !this.password){
                this.info = 'Digite todos os dados solicitados'
            } else {
                return axios.post('http://localhost:8000/api/create-user',{
                    name: this.name,
                    email: this.email,
                    password:  this.password
                },{
                    headers: {
                        'Content-type': 'application/json',
                    }
                }).then((response) => {
                    this.info = response.data
                }
                ).catch(error => {
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