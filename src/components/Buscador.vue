<template>
  <div>
    <input type="text" v-model="username"/>
    <ol>
      <li v-for="field in fields" v-bind:key="field.id">{{ field }}</li>
    </ol>
  </div>
</template>

<script>
export default {
  name: "Buscador",
  props: ['fields']
};
</script>

<style>
</style>