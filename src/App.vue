<script setup>
const name = 'Martin';
const stylecolor = 'color: blue';
const arrayColors = ['blue', 'red', 'green'];
const activo = true;
const arrayFruits = ['apple', 'banana', 'pineaple', 'orange'];

const FruitsListObject = [
  { name: 'manzana', price: '$1.000', description: 'Una manzana', stock: 0 },
  { name: 'Naranja', price: '$2.000', description: 'Una naranja', stock: 10 },
  { name: 'Lulo', price: '$3.000', description: 'Un lulo', stock: 20 },
];

const objectPerson = {
  name: 'Martin',
  email: 'dev.martin@gmail.com',
  phone: 3224682353,
};

const handleClick = (message) => {
  console.log(message);
};
</script>

<template>
  <!-- interpolación de texto -->
  <h1>Holaaa {{ name.toUpperCase() }}</h1>

  <!-- Enlaces de atributos -->
  <h2 :style="stylecolor">Soy azulito</h2>
  <h2 :style="`color: ${arrayColors[2]}`">Soy {{ arrayColors[2] }}</h2>
  <p>{{ arrayColors }}</p>

  <!-- Expresiones de JS -->
  <p>{{ activo ? 'Estoy activo' : 'Estoy inactivo' }}</p>

  <!-- DIRECTIVAS -->
  <!-- V-ELSE debe estar justo después del V-IF -->
  <p v-if="activo">Estoy activo!</p>
  <p v-else>Estoy inactivo!!</p>

  <!-- Esto sirve para mostrar o no algo, pero lo que hace es display: none -->
  <h2 v-show="activo">Estoy activo con v-show</h2>
  ---------------------------------------------------------------

  <ul>
    <li v-for="(fruit, index) in arrayFruits" :key="index">
      {{ index }} - {{ fruit }}
    </li>
  </ul>
  <ul>
    <li v-for="item in FruitsListObject" :key="item.name">
      Fruta: {{ item.name }}, Precio: {{ item.price }}
    </li>
  </ul>
  ---------------------------------------------------------------
  <br />
  El template que funciona como un fragment. v-for con v-if
  <template v-for="item in FruitsListObject" :key="item.name">
    <li v-if="item.stock > 5">
      Fruta: {{ item.name }}, Precio: {{ item.price }}
    </li>
  </template>
  ---------------------------------------------------------------
  <ul>
    <li v-for="(value, property, index) in objectPerson" :key="value">
      {{ property }} - {{ value }}
    </li>
  </ul>

  ---------------------------------------------------------------
  <br />
  <h1>EVENTOS</h1>
  <button @click="handleClick('Texto')">Actívame</button>
  <button @click="handleClick('Left')">Click left</button>
  <button @click.middle="handleClick('Middle')">Click middle</button>
  <button @click.right="handleClick('Right')">Click right</button>
  <br />
  ---------------------------------------------------------------
</template>

<style></style>
