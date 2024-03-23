<template>
  <div>
    <label>{{ label }}</label>
    <Multiselect v-if="isVisible" @selection-change="handleSelectionChange" v-model="selectedOptions"  mode='tags'  :options="options" :placeholder="placeholder" @input="handleChange" />
    <Multiselect v-else v-model="selectedOptions" @selection-change="handleSelectionChange" :options="options" :placeholder="placeholder" @input="handleChange" />
  </div>
</template>
<script>
import Multiselect from '@vueform/multiselect'

export default {
  components: {
    Multiselect,
  },
  props: {
    label: {
      type: String,
      required: true
    },
    placeholder: {
      type: String,
      required: true
    },
    options: {
      type: Array,
      required: true
    },
    isVisible:{
      type:Boolean,
      required:false
    }

  },
  data() {
    return {
      selectedOptions: [],
    }
  },
  methods: {
    handleChange() {
      this.$emit('selection-change', this.selectedOptions); // Emit selected options
    }
  }
}
</script>

<style src="@vueform/multiselect/themes/default.css"></style>