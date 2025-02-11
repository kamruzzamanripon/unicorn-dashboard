<template>
  <select :class="`border-gray-300 focus:border-indigo-500 focus:ring-indigo-500 rounded-md shadow-sm ${className}`"
    v-model="selectedValue" @change="updateValue">
    <option value="">Select Item</option>
    <option v-for="option in options" :key="option">{{ option }}</option>
  </select>
</template>

<script>
export default {
  name: 'SelectInput',
  props: {
    modelValue: {
      type: String,
      default: '',
    },
    className: {
      type: String,
      default: '',
    },
    options: {
      type: Array,
      default: () => [],
    },
  },
  data() {
    return {
      selectedValue: this.modelValue, // Initialize with modelValue
    };
  },
  watch: {
    modelValue(newValue) {
      this.selectedValue = newValue; // Keep in sync with prop changes
    }
  },
  methods: {
    updateValue() {
      this.$emit('update:modelValue', this.selectedValue);
    }
  }
};
</script>
