<template>
    <div class="form-component">
      <form @submit.prevent="handleSubmit">
        <label for="name">Meno: <span class="star">*</span></label>
        <input type="text" v-model="form.name" class="swal2-input" required>
  
        <div class="form-row">
          <div class="form-column">
            <label for="email">E-mail: <span class="star">*</span></label>
            <input type="email" v-model="form.email" class="swal2-input" required>
          </div>
  
          <div class="form-column">
            <label for="phone">Tel. číslo:</label>
            <input type="text" v-model="form.phone" class="swal2-input">
          </div>
        </div>
  
        <label for="website">Webstránka:</label>
        <input type="url" v-model="form.website" class="swal2-input">
  
        <label for="note">Poznámka: <span class="star">*</span></label>
        <textarea v-model="form.note" class="swal2-textarea" required placeholder="Je niečo čo by ste sa nás chceli spýtať?"></textarea>
  
        <div v-if="errorMessage" class="error">{{ errorMessage }}</div>
        <div v-if="successMessage" class="success">{{ successMessage }}</div>
        <br>
        <Button :buttonClass="buttonClass" type="submit">{{ submitText }}</Button>
      </form>
    </div>
  </template>
  
  <script setup lang="ts">
  import { ref, defineProps, defineEmits } from 'vue';
  import Button from '~/components/Button.vue';
  
  const props = defineProps({
    form: {
      type: Object,
      required: true
    },
    errorMessage: {
      type: String,
      default: ''
    },
    successMessage: {
      type: String,
      default: ''
    },
    buttonClass: {
      type: String,
      default: 'cta-button'
    },
    submitText: {
      type: String,
      default: 'Submit'
    }
  });
  
  const emit = defineEmits(['submit']);
  
  const handleSubmit = () => {
    emit('submit');
  };
  </script>
  