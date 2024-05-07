<script setup></script>

<template>
  <button class="btn">
    <slot></slot>
  </button>
</template>

<style scoped>
.btn {
  border-radius: 0.5em;
  border: 4px solid #027373;
  color: #f2e7dc;
  font-weight: black;
  background-color: #038c7f;
  color: #f2e7dc;
  font-size: 1.44rem;
  cursor: pointer;
  transition: transform 250ms ease;

  min-width: 3em;
  min-height: 3em;
}

.btn:hover {
  transform: scale(0.95);
}

.btn--accent {
  background-color: #d55906;
  border: 4px solid #be3406;
}
</style>
