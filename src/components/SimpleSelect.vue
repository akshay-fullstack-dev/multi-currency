<template>
    <select v-model="selectedOptions" @change="handleChange">
        <option v-for="option in options" :key="option.id" :value="option.value">{{ option.label }}</option>
    </select>
</template>
<script>
export default {
    props: {
        options: {
            type: Array,
            required: true
        }
    },
    data() {
        return {
            selectedOptions: []
        };
    },
    methods: {
        handleChange() {
            this.$emit('options-selected', this.selectedOptions);
        }
    }
};
</script>