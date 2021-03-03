<template>
  <div id="app">
    <button v-on:click="getUsers" v-if="!lists.length">Listar</button>
    <input type="text" placeholder="Buscar" v-model="login" />
    <ul>
      <li v-for="item in searchUser" :key="item.id">
        {{ item.login }}
      </li>
    </ul>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "App",
  components: {},
  data() {
    return {
      lists: [],
      login: "",
    };
  },
  methods: {
    getUsers: function () {
      var urlUsers = "https://api.github.com/users";
      axios.get(urlUsers).then((response) => {
        this.lists = response.data;
      });
    },
  },
  computed: {
    searchUser: function () {
      return this.lists.filter((item) => item.login.includes(this.login));
    },
  },
};
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
