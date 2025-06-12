<script setup>
import backgroundVideo from "@/assets/video/mainvisual.mp4";
import VideoBackground from "vue-responsive-video-background-player";
import backgroundImage from "@/assets/images/home-page.png";
import { useRouter } from "vue-router";
const router = useRouter();

function onClick() {
  console.log("cilck");
  router.push("/about");
}
</script>

<template>
  <div class="home" :style="{ backgroundImage: `url('${backgroundImage}')` }" @click="onClick">
    <video-background :src="backgroundVideo" />
  </div>
</template>

<style scoped>
.home {
  background-color: black;
  position: absolute;
  top: 0;
  left: 0;
  height: 100vh;
  width: 100vw;
  background-size: cover;
  background-position: center;
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 2;
  cursor: pointer;
  .vue-responsive-videobg {
    width: 100%;
    height: 100%;
    position: absolute;
    pointer-events: none;
  }
}
</style>
