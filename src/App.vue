<template>
  <div class="container">
    <TheCalculator class="calc"> </TheCalculator>
    <TheResults class="res"></TheResults>
  </div>
</template>

<script setup>
import TheCalculator from './components/TheCalculator.vue';
import TheResults from './components/TheResults.vue';
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
html {
  font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto,
    Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
}
body {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100dvh;
  flex-wrap: wrap;
  text-transform: capitalize;
  background: #e3f4fc;
}
.container {
  max-width: 80vw;
  display: flex;
  background: #ffffff;
  justify-content: center;
  align-items: center;
  padding: 1rem;
  margin: auto;
}
.calc,
.res {
  flex-grow: 1;
  align-self: stretch;
}
.res {
}
</style>
