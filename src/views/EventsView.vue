<template>
  <div class="events-view">
    <div v-if="data[0]" v-for="row in data" class="events-view__row">
      <!-- <ProjectsCard :data="row" /> -->
      <!-- <TresCanvas clear-color="”#82DBC5”" window-size>
        <TresPerspectiveCamera />
        <TresMesh @click="onClick">
          <TresBoxGeometry :args="[1, 1, 1]" />
          <TresMeshNormalMaterial />
        </TresMesh>
      </TresCanvas> -->
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from "vue";
import { TresCanvas } from "@tresjs/core";
const data = ref([]);

onMounted(async () => {
  const response = await (
    await fetch(
      "https://sheets.googleapis.com/v4/spreadsheets/1udZBWWpYj0_yJ3F0LzK6l9GQDuwOBQUDHGAXlFLYXdk/values/past events?alt=json&key=AIzaSyDIhYG3gGUef-YZe_I6aMJ94saRpQI__94"
    )
  ).json();
  data.value = response.values;
});

const onClick = () => {
  console.log("Clicked");
};
</script>

<style lang="scss" scoped>
.events-view {
  color: black;
  height: 100%;
  width: 100%;
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: flex-start;
  overflow-y: auto;
  flex-grow: 1;
  &__row {
    width: 100%;
  }
}
</style>
