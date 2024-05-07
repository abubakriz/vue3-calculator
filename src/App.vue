<script setup>
import { ref } from "vue";
import Button from "./components/Button.vue";

const OPERANDS = ["7", "8", "9", "4", "5", "6", "1", "2", "3", ".", "0"];
const OPERATIONS = ["+", "-", "*", "/", "=", "AC"];
const expression = ref("");

function addOperation(op) {
  if (op == "AC") {
    expression.value = "";
    return;
  }

  if (OPERATIONS.includes(expression.value.at(-1))) {
    return;
  }

  switch (op) {
    case "=":
      expression.value = String(eval(expression.value));
      return;
  }

  expression.value += op;
}

function addOpperand(num) {
  expression.value += num;
}
</script>

<template>
  <div class="container">
    <output class="result">{{ expression }}</output>
    <div class="seperator">
      <div class="numbers-grid">
        <Button v-for="op in OPERANDS" @click="addOpperand(op)">{{
          op
        }}</Button>
      </div>

      <div class="operations-grid">
        <Button
          v-for="op in OPERATIONS"
          @click="addOperation(op)"
          :class="{ 'btn--accent': op == '=' }"
          >{{ op }}</Button
        >
      </div>
    </div>
  </div>
</template>

<style scoped>
.container {
  display: grid;
  place-content: center;
  min-height: 100vh;
  gap: 1rem;
}

.numbers-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  max-width: min-content;
  gap: 0.5rem;
}

.operations-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  max-width: min-content;
  gap: 0.5rem;
}

.seperator {
  display: grid;
  grid-auto-flow: column;
  place-items: start;
  max-width: min-content;
  gap: 2rem;
}

.result {
  font-size: 3rem;
  max-width: min-content;
  font-family: monospace;
  color: #f2e7dc;
  height: 1em;
}
</style>
