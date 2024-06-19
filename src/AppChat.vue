<script setup>
import { ref } from 'vue';
import TemperatureInput from './components/inputNumberChat.vue';

// Initialize temperature values
const kelvin = ref(0);
const celsius = ref(0);
const fahrenheit = ref(32);

// Functions to update temperatures
const updateTemperaturesFromKelvin = (value) => {
  celsius.value = value - 273.15;
  fahrenheit.value = (value - 273.15) * 9/5 + 32;
};

const updateTemperaturesFromCelsius = (value) => {
  kelvin.value = value + 273.15;
  fahrenheit.value = value * 9/5 + 32;
};

const updateTemperaturesFromFahrenheit = (value) => {
  celsius.value = (value - 32) * 5/9;
  kelvin.value = (value - 32) * 5/9 + 273.15;
};
</script>


<template>
    <div>
      <TemperatureInput
        v-model:temperatureValue="kelvin"
        unit="K"
        @update-temperature="updateTemperaturesFromKelvin"
      />
      <TemperatureInput
        v-model:temperatureValue="celsius"
        unit="C"
        @update-temperature="updateTemperaturesFromCelsius"
      />
      <TemperatureInput
        v-model:temperatureValue="fahrenheit"
        unit="F"
        @update-temperature="updateTemperaturesFromFahrenheit"
      />
    </div>
  </template>
  

  