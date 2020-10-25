<template>
  <div id="app">
    <h3>index</h3>
    <router-link to="/home">home</router-link>
    <router-link to="/user">user</router-link>
    <hr>
    <router-view></router-view>
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style>

</style>
