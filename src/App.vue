<script setup>
const name = 'Nombresito dinámico';
const stylecolor = 'color: blue';
</script>

<template>
  <h1>Holaaa {{ name }}</h1>
  <h2 :style="stylecolor">Soy azul</h2>
</template>

<style>
h1 {
  color: red;
}
</style>
