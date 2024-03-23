<template>
  <div class="container mt-5">
    <!-- <multi-select label="Select Options:" :options="options" @selection-change="handleSelectionChange"></multi-select>
    <div class="mt-3">
      <h2>Selected Options:</h2>
      <ul>
        <li v-for="selectedItem in selectedItems" :key="selectedItem.id">{{ selectedItem.name }}</li>
      </ul>
    </div> -->
    <multi-word v-model="selectedItems1" @selectionChanged="handleSelectionChange1" placeholder="slelect currency"
      label="Select Options:" :options="options"></multi-word>
    <multi-word v-model="selectedItems2" :isTags="true" @selectionChanged="handleSelectionChange2"
      placeholder="slelect currency" label="Select Options:" :options="options"></multi-word>
    <button @click="showValue">Select</button>
  </div>
</template>

<script>
// import MultiSelect from './components/MultiSelect.vue';
import MultiWord from './components/MultiWord.vue';

export default {
  components: {
    // MultiSelect,
    MultiWord
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
