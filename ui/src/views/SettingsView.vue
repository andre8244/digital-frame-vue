<script setup>
import { ref, onMounted } from "vue";
import axios from "axios";
import TextInput from "@/components/TextInput.vue";
// import { Input } from "flowbite-vue"; ////

const rootPath = ref("");
const speed = ref(0);

onMounted(() => {
  axios.get("http://raspberrypi:3000/digitalframe/config").then((result) => {
    console.log("get config, result", result.data); ////

    const config = result.data.config; ////
    rootPath.value = config.rootPath;
    speed.value = config.speed;
  });
});
</script>

<template>
  <div>
    <h1 class="text-xl font-bold mb-5">Settings</h1>

    <div>rootPath {{ rootPath }}</div>
    <div>speed {{ speed }}</div>

    <!-- <div>
      <label for="rootPath" class="block mb-2 text-sm font-medium text-gray-200"
        >Root path</label
      >
      <input
        type="text"
        id="rootPath"
        class="bg-gray-800 border border-gray-600 rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5"
        v-model="rootPath"
      />
    </div> -->

    <!-- <Input placeholder="enter your first name" label="First name" /> -->

    <TextInput :id="rootPath" :label="'Root path'" v-model="rootPath" />
    <TextInput :id="speed" :label="'Speed'" v-model="speed" />
  </div>
</template>

<style scoped></style>
