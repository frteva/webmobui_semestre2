<script setup>
import { ref, computed } from 'vue'


const tempSI = ref(0);

const celsius = defineModel('celsius', {
  get() {
    return tempSI.value - 273.15;
  },
  set(value) {
    return tempSI.value + 273.15;
  }

})

const tempFahrenheit = defineModel('fahrenheit', {
  get() {
    return tempSI.value * 9 / 5 - 459.67;
  },
  set(value) {
    tempSI.value = (value + 459.67) * 5 / 9;
  }
});

const tempKelvin = defineModel('kelvin', {
  get() {
    return tempSI.value;
  },
  set(value) {
    tempSI.value = value;
  }
});

</script>


<template>
  
</template>


<style scoped>

  .box {
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .box-temp {
    width: 30%;  /* Exemple de largeur définie */
    margin: 0 auto;
    flex-flow: column;
    text-align: center;
  }

</style>
