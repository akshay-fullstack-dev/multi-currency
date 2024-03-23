<template>
  <div class="container mt-5">
    <currency-option v-model="selectedItems1" @selectionChanged="handleSelectionChange1" placeholder="select currency"
      label="Select Options:" :options="options"></currency-option>
    <currency-option v-model="selectedItems2" :isTags="true" @selectionChanged="handleSelectionChange2"
      placeholder="select currency" label="Select Options:" :options="options"></currency-option>
    <button @click="showValue">Select</button>
  </div>
</template>

<script>
import CurrencyOption from './components/CurrencyOption.vue';

export default {
  components: {
    CurrencyOption
  },
  data() {
    return {
      options: [
        {value: '1', label: 'Option 1' },
        {value: '3', label: 'Option 3' },
        {value: '2', label: 'Option 2' },
        {value: '4', label: 'Option 4' },
        {value: '5', label: 'Option 5' }
      ],
      selectedItems1: [],
      selectedItems2: []
    };
  },
  methods: {
    handleSelectionChange1(selectedItems) {
      this.selectedItems1 = selectedItems; // Update selected items for the first instance
    },
    handleSelectionChange2(selectedItems) {
      this.selectedItems2 = selectedItems; // Update selected items for the second instance
    },
    showValue() {
      console.log(this.selectedItems1)
      console.log(this.selectedItems2)
    }

  }
};
</script>

<style>
/* Add your custom styles here */
</style>
