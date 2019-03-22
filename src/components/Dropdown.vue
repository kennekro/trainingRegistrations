<template>
  <dropdown :options="arrayOfObjects" 
          :selected="object" 
          v-on:updateOption="methodToRunOnSelect" 
          :placeholder="'Select an Item'">
  </dropdown>
</template>

<script>
import dropdown from 'vue-dropdowns';
 
export default {
        data() {
          return {
            arrayOfObjects: [
              {
                name: "First option"
              },
              {
                name: "Second option"
              }
            ],
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
          }
        }
      }
</script> 