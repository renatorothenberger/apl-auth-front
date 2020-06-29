<template>
  <div class="home">
    <p>Bem vindo {{user}}</p>
  </div>
</template>

<script>

export default {
  name: 'Home',
  data() {
      return {
          user: ''
      };
  },
  mounted() {
    this.user = sessionStorage.getItem('userName')
  },
}
</script>
