<template>
  <div>
    <p>Username: {{username}}</p>
    <p>Avatar: {{avatar}}</p>
    <hr>
  </div>
</template>

<script>
export default {
    name: "Usuarios",
    props: ['username', 'avatar']

}
</script>

<style>

</style>