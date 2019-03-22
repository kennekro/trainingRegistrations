<template>
  <div id="app">
    <Dropdown />
    <RegistrationTable />
    <button id="registerButton" v-on:click="deliverData()">Registrer</button>
  </div>
</template>

<script>
var value = 0;

import Dropdown from './components/Dropdown.vue'
import RegistrationTable from './components/RegistrationTable.vue'

export default {
  name: 'app',
  components: {
    Dropdown,
    RegistrationTable
  },
  methods: {
    deliverData(){
      value++;
      alert('Funksjonen er kalt, value er: ' + value)
    }
  }
}

</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
