<template>
  <dropdown :options="arrayOfObjects" 
    :selected="object" 
    v-on:updateOption="methodToRunOnSelect" 
    :placeholder="'Select an Item'">
  </dropdown>
  <!--select id="exercise-selector"></select>-->
</template>

<script>
import dropdown from 'vue-dropdowns';
const fb = require('../../firebaseConfig.js')

var fbArray = []
fb.exerciseCollection.where('active', '==', true).get().then(function(querySnapshot) {
  querySnapshot.forEach(function(doc) {
    fbArray.push({name: doc.data().name, repetitions: doc.data().exerciseRepetitions})
  });
})
.catch(function(error) {
  console.error("Error getting documents: ", error);
});

export default {
  data() {
    return {
      arrayOfObjects: fbArray,
      object: {
        name: 'Select exercise',
      }
    }
  },
  components: {
      'dropdown': dropdown,
  },
  methods: {
    methodToRunOnSelect(payload) {
      this.object = payload;
      this.$emit('exerciseSelected', payload.name)
    }
  }
}
</script> 