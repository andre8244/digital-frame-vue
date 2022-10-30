<script setup>
import { ref, onMounted } from "vue";
import axios from "axios";
import { Button } from "flowbite-vue";

const albums = ref([]);

onMounted(() => {
  axios.get("http://raspberrypi:3000/digitalframe/list").then((result) => {
    console.log("get list, result", result.data.albums); ////

    albums.value = result.data.albums.reverse();
  });
});

function play(album) {
  console.log("play", album); ////

  const albumEncoded = encodeURIComponent(album);

  console.log("albumEncoded", albumEncoded); ////

  axios
    .put(`http://raspberrypi:3000/digitalframe/play/${albumEncoded}`)
    .then((result) => {
      console.log("put play, result", result); ////
    });
}

function setConfig() {
  ////
  const newConfig = {
    rootPath: "/media/andre/OneTouch4/digitalframe-images_sssss",
    speed: 50,
  };

  axios
    .put("http://raspberrypi:3000/digitalframe/config", newConfig)
    .then((result) => {
      console.log("put config, result", result); ////
    });
}

function setDefaultConfig() {
  axios
    .put("http://raspberrypi:3000/digitalframe/defaultConfig")
    .then((result) => {
      console.log("put default config, result", result); ////
    });
}
</script>

<template>
  <div class="grid gap-5 grid-cols-1 md:grid-cols-2 xl:grid-cols-3">
    <!-- <Button @click="setConfig">Set config</Button> ////
    <Button @click="setDefaultConfig">Set default config</Button> -->
    <div
      v-for="(album, index) in albums"
      :key="index"
      class="bg-blue-700 hover:bg-blue-800 px-3 py-8 rounded-sm cursor-pointer"
      @click="play(album)"
    >
      {{ album }}
    </div>
  </div>
</template>

<style scoped></style>
