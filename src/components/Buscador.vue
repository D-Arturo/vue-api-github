<template>
  <div>
    <input type="text" v-model="users">
    <ol>
      <li 
      v-for="repo in repos"
      v-bind:key="repo.id"
      >{{repo}}</li>
    </ol>
  </div>
</template>

<script>
export default {
    name: 'Buscador',
    props: ['users', 'repos']

}
</script>

<style>

</style>