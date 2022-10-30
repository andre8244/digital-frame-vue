<script setup>
defineProps({
  id: {
    type: String,
    required: true,
    value: String,
  },
  label: {
    type: String,
    required: true,
  },
  placeholder: {
    type: String,
    required: false,
  },
});
</script>

<template>
  <div>
    <label :for="id" class="block mb-2 text-sm font-medium text-gray-200">{{
      label
    }}</label>
    <input
      type="text"
      :id="id"
      :value="value"
      @input="(event) => (value = event.target.value)"
      class="bg-gray-800 border border-gray-600 rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5"
      :placeholder="placeholder"
    />
  </div>
</template>

<style></style>
