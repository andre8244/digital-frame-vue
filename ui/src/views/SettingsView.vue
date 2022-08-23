<script setup>
import TextInput from "@/components/TextInput.vue";
</script>

<template>
  <div>
    <h1 class="text-xl font-bold mb-5">Settings</h1>

    <TextInput :id="rootPath" :label="'Root path'" />
  </div>
</template>

<style scoped></style>
