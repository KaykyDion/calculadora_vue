<script setup>
import { reactive } from "vue";

const state = reactive({
  number_a: 0,
  number_b: 0,
  operator: "+",
  result: 0,
});

const sum = () => {
  if (state.number_a === "") {
    state.number_a = 0;
  } else if (state.number_b === "") {
    state.number_b = 0;
  }

  return (state.result = eval(
    `${parseFloat(state.number_a)} ${state.operator} ${parseFloat(
      state.number_b
    )}`
  ));
};
</script>

<template>
  <div class="container mt-5 ms-5">
    <header>
      <h1>Calculadora aritimética VueJS</h1>
    </header>
    <div class="row d-flex align-items-center">
      <div class="col-md-4">
        <input
          @input="(ev) => (state.number_a = ev.target.value)"
          type="number"
          class="form-control number-a"
        />
      </div>
      <div
        @change="(ev) => (state.operator = ev.target.value)"
        class="col-md-1"
      >
        <select class="form-control">
          <option value="+">+</option>
          <option value="-">-</option>
          <option value="*">*</option>
          <option value="/">/</option>
        </select>
      </div>
      <div class="col-md-4">
        <input
          @input="(ev) => (state.number_b = ev.target.value)"
          type="number"
          class="form-control number-b"
        />
      </div>
      <div class="col-md-1">
        <h2>=</h2>
      </div>
      <div class="col-md-2">
        <h2 class="result">{{ sum() }}</h2>
      </div>
    </div>
  </div>
</template>

<style scoped></style>
