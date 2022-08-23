<script setup>
import { RouterLink, RouterView, useRoute } from "vue-router";
import { computed } from "vue";
import { Button } from "flowbite-vue";

const route = useRoute();

const isSettingsDisabled = computed(() => {
  return route.name === "settings";
});
</script>

<template>
  <div class="p-5">
    <nav class="mb-8 flex justify-between items-center">
      <RouterLink to="/" class="font-bold text-2xl">Digital Frame</RouterLink>
      <RouterLink
        :is="isSettingsDisabled ? 'span' : 'router-link'"
        to="/settings"
      >
        <Button :disabled="isSettingsDisabled">Settings</Button>
      </RouterLink>
    </nav>
    <RouterView />
  </div>
</template>

<style></style>
