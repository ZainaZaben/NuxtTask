<template>
    <button
      :class="['button', buttonClass]"
      @click="handleClick"
      :type="type"
    >
      <slot></slot>
    </button>
  </template>
  
  <script setup>
  import { defineProps, defineEmits } from 'vue';
  
  const props = defineProps({
    buttonClass: {
      type: String,
      default: ''
    },
    type: {
      type: String,
      default: 'button'
    }
  });
  
  const emit = defineEmits(['click']);
  
  const handleClick = (event) => {
    emit('click', event);
  };
  </script>
  