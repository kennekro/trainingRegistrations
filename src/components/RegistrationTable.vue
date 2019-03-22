<template>
  <table id="registrationTable" align="center">
    <tr>
      <th>Set 1</th>
      <th>Set 2</th>
      <th>Set 3</th>
    </tr>
    <tr>
      <td >
          <input v-model="firstSetValue" v-on:change="firstSetValueChanged(firstSetValue)" >kg
          <p>Value is: {{firstSetValue}} </p>
      </td>
      <td >
          <input v-model="secondSetValue" v-on:change="secondSetValueChanged(secondSetValue)" >kg
          <p>Value is: {{secondSetValue}} </p>
      </td>
      <td >
          <input v-model="thirdSetValue" v-on:change="thirdSetValueChanged(thirdSetValue)" >kg
          <p>Value is: {{thirdSetValue}} </p>
      </td>
    </tr>
  </table>
</template>

<script>
var setValues = [0,0,0];
export default {
  name: 'app',
  data() {
    return {
      firstSetValue: '',
      secondSetValue: '',
      thirdSetValue: ''
    }
  },
  methods: {
    firstSetValueChanged(payload) {
      setValues[0] = payload;
      this.$emit('setsChanged', setValues)
    },
    secondSetValueChanged(payload) {
      setValues[1] = payload;
      this.$emit('setsChanged', setValues)
    },
    thirdSetValueChanged(payload) {
      setValues[2] = payload;
      this.$emit('setsChanged', setValues)
    }
  }
}
</script>

<style>
#registrationTable {
  text-align: center;
}
</style>