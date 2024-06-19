<script setup>
import { defineProps, defineEmits, watch } from 'vue';

// Define props
const props = defineProps({
  temperatureValue: Number,
  unit: String,
});

// Define emits
const emit = defineEmits(['update-temperature']);

// Watch for changes in temperatureValue to emit the update event
watch(() => props.temperatureValue, (newValue) => {
  emit('update-temperature', parseFloat(newValue));
});

// Emit update event on input
const onInput = (event) => {
  const newValue = parseFloat(event.target.value);
  emit('update-temperature', newValue);
};
</script>


<template>
    <div>
      <label :for="unit">{{ unit }}</label>
      <input
        :id="unit"
        type="number"
        :value="temperatureValue"
        @input="onInput"
      />
    </div>
  </template>
  