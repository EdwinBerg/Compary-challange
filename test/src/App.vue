<template>
  <div id="app">
    <compary-card />
  </div>
</template>

<script>
import ComparyCard from "./components/ComparyCard.vue";

export default {
  name: "App",
  components: {
    ComparyCard,
  },
};
</script>

<style>
@import "./assets/style.css";
</style>
