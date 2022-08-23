<script setup></script>

<template>
  <div class="grid gap-5 grid-cols-1 md:grid-cols-2 xl:grid-cols-3">
    <div
      v-for="item in 12"
      :key="item"
      class="bg-blue-700 hover:bg-blue-800 px-3 py-8 rounded-sm cursor-pointer"
    >
      Test album
    </div>
  </div>
</template>

<style scoped></style>
