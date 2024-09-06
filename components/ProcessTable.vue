<template>
    <table class="process-table">
      <tr v-for="(step, index) in steps" :key="index" :class="getRowClass(index)">
        <td v-if="isOdd(index) && step.arrow && !isLastRow(index)" class="arrow">
          <img :src="step.arrow" alt="arrow" />
        </td>
        <td class="number" v-if="step.numberImage">
          <img :src="step.numberImage" :alt="'Step ' + (index + 1)" class="step-number" />
        </td>
        <td class="content">
          <h2>{{ step.title }}</h2>
          <p v-html="step.description"></p>
        </td>
        <td v-if="isEven(index) && step.arrow && !isLastRow(index)" class="arrow">
          <img :src="step.arrow" alt="arrow" />
        </td>
      </tr>
    </table>
  </template>
  
  <script>
  export default {
    props: {
      steps: {
        type: Array,
        required: true,
        default: () => []
      }
    },
    methods: {
      isEven(index) {
        return index % 2 === 0;
      },
      isOdd(index) {
        return index % 2 !== 0;
      },
      getRowClass(index) {
        return this.isEven(index) ? 'even' : 'odd';
      },
      isLastRow(index) {
        return index === this.steps.length - 1;
      }
    }
  };
  </script>
  