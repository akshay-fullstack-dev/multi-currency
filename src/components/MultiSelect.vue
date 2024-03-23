<template>
  <div>
    <label>{{ label }}</label>
    <!-- Dropdown Toggle Button -->
    <div class="dropdown" ref="dropdown">
      <button class="btn btn-secondary dropdown-toggle" type="button" id="dropdownMenuButton" aria-haspopup="true" aria-expanded="false" @click="toggleDropdown">
        Select options
      </button>
      <div class="dropdown-menu" aria-labelledby="dropdownMenuButton">
        <!-- Options -->
        <div v-for="item in options" :key="item.id" class="dropdown-item" @click="toggleSelection(item)">
          {{ item.name }}
        </div>
      </div>
    </div>
    <!-- Selected Tags -->
    <div class="mt-2">
      <span v-for="selectedItem in selectedItems" :key="selectedItem.id" class="badge bg-primary me-1">
        {{ selectedItem.name }}
        <button type="button" class="btn-close btn-close-white" aria-label="Close" @click="removeSelection(selectedItem)"></button>
      </span>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    label: {
      type: String,
      required: true
    },
    options: {
      type: Array,
      required: true
    }
  },
  data() {
    return {
      selectedItems: [],
      isDropdownOpen: false
    };
  },
  mounted() {
    // Close dropdown when clicked outside
    document.addEventListener('click', this.handleClickOutside);
  },
  beforeUnmount() {
    document.removeEventListener('click', this.handleClickOutside);
  },
  methods: {
    toggleDropdown() {
      console.log('toggleDropdown method called');
      this.isDropdownOpen = !this.isDropdownOpen;
    },
    toggleSelection(item) {
      const index = this.selectedItems.findIndex(selectedItem => selectedItem.id === item.id);
      if (index === -1) {
        this.selectedItems.push(item);
      } else {
        this.selectedItems.splice(index, 1);
      }
    },
    removeSelection(item) {
      const index = this.selectedItems.findIndex(selectedItem => selectedItem.id === item.id);
      if (index !== -1) {
        this.selectedItems.splice(index, 1);
      }
    },
    handleClickOutside(event) {
      if (this.$refs.dropdown && !this.$refs.dropdown.contains(event.target)) {
        this.isDropdownOpen = false;
      }
    }
  }
};
</script>

<style>
.dropdown-item {
  cursor: pointer;
}
</style>
