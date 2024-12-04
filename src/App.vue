<template>
  <div class="container">
    <TheCalculator class="calc" @sumbitData="getData"> </TheCalculator>
    <TheResults class="res" :monthlyPay="monthlyPay"></TheResults>
  </div>
</template>

<script setup>
import TheCalculator from './components/TheCalculator.vue';
import TheResults from './components/TheResults.vue';
import { ref } from 'vue';
const loanData = ref({});
const monthlyPay = ref('');
const getData = (data) => {
  loanData.value = data;
  calculateLoan();
};
const calculateLoan = () => {
  let m;
  const p = parseFloat(loanData.value.amount) || 0;
  const r = parseFloat(loanData.value.percentage) / 1200 || 0;
  const n = parseFloat(loanData.value.years, 10) * 12 || 1;

  if (r === 0) {
    m = p / n;
  } else {
    const top = r * Math.pow(1 + r, n);
    const bottom = Math.pow(1 + r, n) - 1;
    m = (p * (top / bottom)).toFixed(2);
  }
  monthlyPay.value = m;
};
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
