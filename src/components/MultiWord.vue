<template>
  <div>
    <label>{{ label }}</label>
    <Multiselect v-if="isTags" @select="handleSelectionChange" @selection-change="handleSelectionChange"
      v-model="selectedOptions" mode='tags' :options="options" :placeholder="placeholder" />
    <Multiselect v-else v-model="selectedOptions" @select="handleSelectionChange"
      @selection-change="handleSelectionChange" :options="options" :placeholder="placeholder" />
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
    isTags: {
      type: Boolean,
      required: false
    }

  },
  data() {
    return {
      selectedOptions: [],
    }
  },
  methods: {
    handleSelectionChange() {
      this.$emit('selectionChanged', this.selectedOptions); // Emit selected options
    }
  }
}
</script>

<style src="@vueform/multiselect/themes/default.css"></style>