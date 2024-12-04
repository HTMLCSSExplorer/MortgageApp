<template>
  <div class="result">
    <img src="../assets/images/illustration-empty.svg" alt="" />

    <h2 v-if="Object.keys(props.monthlyPay).length === 0">
      Results will be shows here
    </h2>
    <h2 v-else>
      <span class="fas fa-sterling-sign"></span>
      <span>{{ props.monthlyPay }}</span>
    </h2>
    <p>
      Lorem ipsum dolor sit amet consectetur, adipisicing elit. Modi, pariatur!
    </p>
  </div>
</template>

<script setup>
const props = defineProps(['monthlyPay']);

console.log(props.monthlyPay);
</script>

<style>
.result {
  width: 100%;
  background: #133040;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  padding: 2rem;
  border-bottom-left-radius: 100px;
}
img {
  width: 70%;
}
h2 {
  font-size: 1.25rem;
  color: white;
  margin-block: 1rem;
}
p {
  text-align: center;
  color: white;
}
</style>
