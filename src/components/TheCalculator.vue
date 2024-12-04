<template>
  <div class="calculator">
    <h1>Mortgage Calculator</h1>
    <form action="" @submit.prevent="calculateLoan">
      <small>mortgage amount</small>
      <div class="form-control">
        <div>
          <span class="fas fa-sterling-sign sign"></span>
          <input type="text" v-model.trim="data.amount" />
        </div>
      </div>
      <div class="form-control">
        <small>mortgage term</small>
        <div class="terms-child">
          <input type="text" v-model.trim="data.years" />
          <span class="sign">years</span>
        </div>
        <small>mortgage interest</small>
        <div class="terms-child">
          <input type="text" v-model.trim="data.percentage" />
          <span class="sign">%</span>
        </div>
      </div>
      <div class="radio-group">
        <label>
          <input
            type="radio"
            name="mortgageType"
            value="repayment"
            checked
            v-model="data.repayment"
          />
          Repayment
        </label>
        <label>
          <input
            type="radio"
            name="mortgageType"
            value="interestOnly"
            v-model="data.interest"
          />
          Interest Only
        </label>
      </div>
      <button>
        <span class="fas fa-calculator"></span> calculate repayments
      </button>
    </form>
  </div>
</template>

<script setup>
import { reactive } from 'vue';
const emit = defineEmits(['sumbitData']);
const data = reactive({
  amount: '',
  years: '',
  percentage: '',
  repayment: false,
  interest: false,
});

const calculateLoan = () => {
  emit('sumbitData', data);
  data.amount = '';
  data.years = '';
  data.percentage = '';
  data.repayment = false;
  data.interest = false;
};
</script>

<style scoped>
h1 {
  font-size: 1rem;
}
.calculator {
  display: flex;
  flex-direction: column;
  width: 100%;
  flex-direction: column;
  justify-content: space-around;
  padding: 1rem;
}
.form-control div {
  display: flex;
  border: 1px solid rgb(119, 115, 115);
  border-radius: 5px;
  overflow: hidden;
  align-items: center;
  margin-bottom: 0.5rem;
  margin-top: 0.25rem;
}
.form-control {
  .terms-child {
    display: flex;
    margin-bottom: 0.5rem;
    margin-top: 0.25rem;
  }
}
input {
  border: 0;
  outline: 0;
  padding: 0.55rem;
  font-size: 1rem;
  flex-grow: 1;
}
.sign {
  background: #e6f2fe;
  padding: 0.75rem;
  text-align: center;
  font-weight: 600;
}
.checks {
  border: 1px solid rgb(119, 115, 115);
  margin-top: 0.5rem;
  padding: 0.5rem;
}
button {
  border: 0;
  padding: 0.75rem 0.5rem;
  margin-top: 1rem;
  width: 100%;
  text-transform: capitalize;
  text-align: center;
  background: #d9db30;
  color: #133040;
  font-weight: 600;
  border-radius: 30px;
  cursor: pointer;
}
.fa-calculator {
  margin-right: 10px;
}
</style>
