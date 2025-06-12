<template>
  <div class="radio-view">
    <div v-if="data[0]" v-for="row in data" class="radio-view__row">
      <ProjectsCard :data="row" />
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from "vue";
import ProjectsCard from "@/components/ProjectCard.vue";
const data = ref([]);

onMounted(async () => {
  const response = await (
    await fetch(
      "https://sheets.googleapis.com/v4/spreadsheets/1udZBWWpYj0_yJ3F0LzK6l9GQDuwOBQUDHGAXlFLYXdk/values/HKCR residency?alt=json&key=AIzaSyDIhYG3gGUef-YZe_I6aMJ94saRpQI__94"
    )
  ).json();
  data.value = response.values.filter((item) => item[1] === "radio");
});
</script>

<style lang="scss" scoped>
.radio-view {
  color: white;
  height: 100%;
  width: 100%;
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: flex-start;
  overflow-y: auto;
  &__row {
    width: 100%;
  }
}
</style>
