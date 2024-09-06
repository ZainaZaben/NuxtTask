<template>
    <ul>
        <li v-for="(item, index) in items" :key="index">{{ item }}</li>
    </ul>
</template>

<script setup>
import { defineProps } from 'vue';


const props = defineProps({
    items: {
        type: Array,
        required: true
    }
});
</script>

