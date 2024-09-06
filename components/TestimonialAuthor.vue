<template>
  <div class="testimonial-container">
    <div class="testimonial" v-for="author in authors" :key="author.name">
      <div :class="`author ${author.name}`">
        <img :src="author.pic" :alt="author.name" class="author-img">
        <div class="author-info">
          <p><strong>{{ author.name }}</strong></p>
          <p>{{ author.title }} <span class="company">{{ author.company }}</span></p>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
const props = defineProps({
  authors: {
    type: Array,
    required: true,
    default: () => []
  }
});

console.log(props);
</script>
