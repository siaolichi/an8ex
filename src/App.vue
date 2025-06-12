<script setup>
import { RouterLink, RouterView } from "vue-router";
import { useRoute } from "vue-router";
import { computed, reactive } from "vue";
import Footer from "@/components/Footer.vue";

const route = useRoute();
const path = computed(() => route.path);
const name = computed(() => route.name);
const state = reactive({ active: false });

const toggleActive = () => {
  state.active = !state.active;
};
</script>

<template>
  <div class="app-wrapper">
    <header>
      <nav v-if="path !== '/'">
        <RouterLink to="/about" @click="toggleActive">About</RouterLink>
        <RouterLink to="/events" @click="toggleActive">Past Projects</RouterLink>
        <RouterLink to="/radio" @click="toggleActive">Radio</RouterLink>
        <RouterLink to="/festival" @click="toggleActive">Festival</RouterLink>
      </nav>
    </header>
    <Footer />
    <RouterView />
  </div>
</template>

<style scoped>
body {
}

.app {
  color: white;
}
.app-wrapper {
  background-color: black;
  width: 100%;
  height: 100vh;
  position: relative;
}
header {
  position: fixed;
  nav {
    display: flex;
    flex-direction: column;
    margin: 10px;
    font-size: 4rem;
    line-height: 5rem;
    text-stroke: 1px white;
    -webkit-text-stroke: 1px white;

    a {
      color: transparent;
    }
    a.router-link-active {
      color: white;
      text-stroke: none;
      -webkit-text-stroke: none;
      text-shadow: white 1px 1px;
    }
  }
}
</style>
