<template>
  <div id="app">

    <Usuarios 
    v-for="usuario in usuarios"
    v-bind:key="usuario.id"
    :username="usuario.login"
    :avatar="usuario.avatar_url"
    />
  </div>
</template>

<script>

import axios from 'axios'
import Usuarios from './components/Usuarios'

export default {
  name: 'App',
  components: {
    Usuarios
  },
  data(){
    return{
      usuarios:[],
    }
  },
  methods:{
    getUsers(){
      axios.get('https://api.github.com/users')
      .then((respuesta) => this.usuarios = respuesta.data)
    }
  },
  mounted(){
    this.getUsers()
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
