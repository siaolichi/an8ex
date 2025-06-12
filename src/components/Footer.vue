<template>
  <footer>
    <a href="https://www.instagram.com/an8x.core/"> <img :src="instagramImg" alt="instagram" height="30px" /></a>
    <a href="https://soundcloud.com/an8x-core"><img :src="soundCloudImg" alt="soundcloud" height="28px" /></a>
    <a href="https://ra.co/promoters/117459"><img :src="rdImg" alt="resident-advisor" height="28px" /></a>
    <a href="mailto:hi@an8x.com"><img :src="emailImg" alt="email" height="28px" /></a>
    <a href="https://t.me/an8xcore"><img :src="telegram" alt="resident-advisor" height="28px" /></a>
  </footer>
</template>

<script setup>
import instagramImg from "@/assets/logo/instagram.svg";
import soundCloudImg from "@/assets/logo/soundcloud.svg";
import rdImg from "@/assets/logo/resident-advisor.svg";
import emailImg from "@/assets/logo/email.svg";
import telegram from "@/assets/logo/telegram.svg";

import { defineProps } from "vue";

const { page } = defineProps({
  page: String,
});
</script>

<style lang="scss" scoped>
footer {
  width: 100%;
  padding: 10px;
  display: flex;
  justify-content: flex-start;
  align-items: center;
  position: fixed;
  bottom: 0;
  left: 0;
  img {
    margin: 10px;
  }
}
</style>
