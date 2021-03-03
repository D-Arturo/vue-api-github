<template>
  <div id="app">
    <input type="text" v-model="username" placeholder="buscador username" />
    <ol>
      <li v-for="repo in repos" v-bind:key="repo.id">{{ repo.name }}</li>
    </ol>
  </div>
</template>

<script>
function queryGithubAPI(username) {
  return fetch(
    `https://api.github.com/users/${username}/repos`
  ).then((response) => response.json());
}

export default {
  name: "App",
  data() {
    return {
      username: "",
      repos: [],
    };
  },
  watch: {
    username: function () {
      queryGithubAPI(this.username).then((repos) => {
        if (repos.length > 0 && repos[0].id) {
          this.repos = repos;
        }
      });
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
