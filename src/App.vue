<template>
  <ul>
    <li v-for="(value, key) in person" :key="key">
      {{key}} -- {{value}}
    </li>
  </ul>
  <button @click="person.age = 18">按钮</button>
</template>

<script>

export default {
  name: 'App',
  data() {
    return {
      person: {
        name: 'jack'
      }
    }
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
