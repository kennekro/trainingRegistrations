<template>
  <div id="app">
    <Dropdown v-on:exerciseSelected="value => this.dropdownValue = value" />
    <RegistrationTable v-on:setsChanged="value => this.setArray = value" />
    <button id="registerButton" v-on:click="addRegistration()">Registrer</button>
  </div>
</template>


<script>
import moment from 'moment'
//import firebase from 'firebase'
import Dropdown from './components/Dropdown.vue'
import RegistrationTable from './components/RegistrationTable.vue'
const fb = require('../firebaseConfig.js')

var date = moment().format('YYYY-MM-DD_HH-mm')
console.log(date)

export default {
  name: 'app',
  data(){
    return{
      dropdownValue: '',
      setArray: [0,0,0]
    }
  },
  components: {
    Dropdown,
    RegistrationTable
  },
  methods: {
    deliverData(){      
      console.info(this.dropdownValue);
      console.info(this.setArray);
    },
    addRegistration() {
      var date = moment().format('YYYY-MM-DD_HH-mm')
      fb.registrationCollection.doc(date).set({
        exercise: this.dropdownValue,
        weightSet: this.setArray
      })
      .then(() => console.log('Document successfully written!'))
      .catch(() => console.error('Error writing document', error));
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
