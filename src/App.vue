<template>
  <div id="app">
    <Dropdown v-on:exerciseSelected="value => this.dropdownValue = value" />
    <RegistrationTable v-on:setsChanged="value => this.setArray = value" />
    <button id="registerButton" v-on:click="deliverData()">Registrer</button>
  </div>
</template>

<script>
import Dropdown from './components/Dropdown.vue'
import RegistrationTable from './components/RegistrationTable.vue'
//import azure from 'azure-storage'

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
      //var firstSet = this.setArray[0].toString();
      //var secondSet = this.setArray[1].toString();

      var azure = require('azure-storage'); 
      var tableService = azure.createTableService();
      var entGen = azure.TableUtilities.entityGenerator;
      var entity = {
        PartitionKey: entGen.String('Test'),
        RowKey: entGen.String('1'),
        description: entGen.String('Test1')
      };

      tableService.insertEntity('registrations', entity, function(error, result, response) {
        if (!error) {
          console.log('Verdi satt inn: ' + result)
        }
        else {
          console.log('Error: ' + error.toString());
        }
      });
      console.log("Button pressed");
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
