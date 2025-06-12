<template>
  <div class="event-card">
    <div class="event-card__top" @click="toggleActive">
      <div class="event-card__title">{{ data[0] }}</div>
      <div class="event-card__year">{{ data[3] }}, {{ data[4] }}</div>
    </div>
    <div class="event-card__bottom" :class="state.active ? '' : 'hide'">
      <div class="event-card__bottom-inner">
        <div style="width: 100%; text-align: right">
          <b>{{ data[1] }}</b> in
          {{ data[2] }}
        </div>
        <p v-html="data[5] && data[5].replace(new RegExp('\r?\n', 'g'), '<br />')"></p>
        <p v-html="data[6] && data[6].replace(new RegExp('\r?\n', 'g'), '<br />')"></p>
        <p v-html="data[7] && data[7].replace(new RegExp('\r?\n', 'g'), '<br />')"></p>
        <br />
        <b>Artists:</b>
        <p v-html="data[8] && data[8].replace(new RegExp('\r?\n', 'g'), '<br />')"></p>
        <br />
      </div>
    </div>
  </div>
</template>

<script setup>
import { defineProps, reactive, ref } from "vue";

const props = defineProps({
  data: Array,
});

const state = reactive({ active: false });

const toggleActive = () => {
  state.active = !state.active;
};
</script>

<style lang="scss" scoped>
.event-card {
  display: flex;
  flex-direction: column;
  justify-content: center;
  width: 99%;

  &__top {
    font-weight: 600;
    padding: 10px;
    margin: 1px;
    border: solid 1px black;
    display: flex;
    justify-content: space-between;
    cursor: pointer;

    &:hover {
      background-color: black;
      color: white;
    }
  }
  &__bottom {
    display: grid;
    grid-template-rows: 1fr;
    transition: grid-template-rows 0.5s ease-out;
    margin: 10px;
    &.hide {
      grid-template-rows: 0fr;
      margin: 0;
    }
  }
  &__bottom-inner {
    overflow: hidden;
    width: 90%;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: flex-start;
  }
}
</style>
