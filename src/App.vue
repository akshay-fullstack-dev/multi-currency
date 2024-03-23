<template>
  <div class="container mt-5">
    <!-- <multi-select label="Select Options:" :options="options" @selection-change="handleSelectionChange"></multi-select>
    <div class="mt-3">
      <h2>Selected Options:</h2>
      <ul>
        <li v-for="selectedItem in selectedItems" :key="selectedItem.id">{{ selectedItem.name }}</li>
      </ul>
    </div> -->
    <multi-word v-model="selectedItems"  @selection-change="handleSelectionChange" placeholder="slelect currency" label="Select Options:" :options="options"></multi-word>
    <multi-word v-model="selectedItems" :isVisible="true"  @selection-change="handleSelectionChange" placeholder="slelect currency" label="Select Options:" :options="options"></multi-word>
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
        { id: 1, value: 'Option 1', label: 'Option 1' },
        { id: 2, value: 'Option 2', label: 'Option 2' },
        { id: 3, value: 'Option 3', label: 'Option 3' },
        { id: 4, value: 'Option 4', label: 'Option 4' },
        { id: 5, value: 'Option 5', label: 'Option 5' }
      ],
      selectedItems: []
    };
  },
  methods: {
    handleSelectionChange(selectedItems) {
      this.selectedItems = selectedItems;
      console.log(this.selectedItems)
    },
    showValue() {
      console.log(this.selectedItems)
    }

  }
};
</script>

<style>
/* Add your custom styles here */
</style>
