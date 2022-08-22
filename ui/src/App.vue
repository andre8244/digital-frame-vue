<script setup>
import { RouterLink, RouterView } from "vue-router";
</script>

<template>
  <div class="px-3">
    <nav class="my-3 flex justify-between">
      <RouterLink to="/" class="font-bold">Digital Frame</RouterLink>
      <RouterLink
        to="/settings"
        class="inline-block rounded-lg px-5 py-2 bg-gray-600 tracking-wider font-semibold"
      >
        Settings
      </RouterLink>
    </nav>
    <RouterView />
  </div>
</template>

<style></style>
