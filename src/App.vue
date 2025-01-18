<script setup>
import { ref, computed } from 'vue';
// const name = 'Martin';
// const stylecolor = 'color: blue';
// const arrayColors = ['blue', 'red', 'green'];
// const activo = true;
// const arrayFruits = ['apple', 'banana', 'pineaple', 'orange'];

// const FruitsListObject = [
//   { name: 'manzana', price: '$1.000', description: 'Una manzana', stock: 0 },
//   { name: 'Naranja', price: '$2.000', description: 'Una naranja', stock: 10 },
//   { name: 'Lulo', price: '$3.000', description: 'Un lulo', stock: 20 },
// ];

// const objectPerson = {
//   name: 'Martin',
//   email: 'dev.martin@gmail.com',
//   phone: 3224682353,
// };

// const handleClick = (message) => {
//   console.log(message);
// };

const counter = ref(0);
const arrayFavorites = ref([]);

const handleCounter = (operation) => {
  if (operation === 'increment') {
    counter.value++;
  } else if (operation === 'decrement') {
    counter.value--;
  } else if (operation === 'reset') {
    counter.value = 0;
  }
};

const add = () => {
  arrayFavorites.value.push(counter.value);
};

const bloqAddBtn = computed(() => {
  const numSearch = arrayFavorites.value.find((num) => num === counter.value);
  if (numSearch === 0) {
    return true;
  }
  return numSearch ? true : false;
});

const classCounter = computed(() => {
  return counter.value > 0
    ? 'positive'
    : counter.value < 0
    ? 'negative'
    : 'zero';
});
</script>

<template>
  <!-- interpolación de texto -->
  <!-- <h1>Holaaa {{ name.toUpperCase() }}</h1> -->

  <!-- Enlaces de atributos -->
  <!-- <h2 :style="stylecolor">Soy azulito</h2>
  <h2 :style="`color: ${arrayColors[2]}`">Soy {{ arrayColors[2] }}</h2>
  <p>{{ arrayColors }}</p> -->

  <!-- Expresiones de JS -->
  <!-- <p>{{ activo ? 'Estoy activo' : 'Estoy inactivo' }}</p> -->

  <!-- DIRECTIVAS -->
  <!-- V-ELSE debe estar justo después del V-IF -->
  <!-- <p v-if="activo">Estoy activo!</p>
  <p v-else>Estoy inactivo!!</p> -->

  <!-- Esto sirve para mostrar o no algo, pero lo que hace es display: none -->
  <!-- <h2 v-show="activo">Estoy activo con v-show</h2> -->
  <!-- --------------------------------------------------------------- -->

  <!-- <ul>
    <li v-for="(fruit, index) in arrayFruits" :key="index">
      {{ index }} - {{ fruit }}
    </li>
  </ul>
  <ul>
    <li v-for="item in FruitsListObject" :key="item.name">
      Fruta: {{ item.name }}, Precio: {{ item.price }}
    </li>
  </ul> -->
  <!-- --------------------------------------------------------------- -->
  <!-- <br />
  El template que funciona como un fragment. v-for con v-if
  <template v-for="item in FruitsListObject" :key="item.name">
    <li v-if="item.stock > 5">
      Fruta: {{ item.name }}, Precio: {{ item.price }}
    </li>
  </template> -->
  <!-- --------------------------------------------------------------- -->
  <!-- <ul>
    <li v-for="(value, property, index) in objectPerson" :key="value">
      {{ property }} - {{ value }}
    </li>
  </ul> -->

  <!-- --------------------------------------------------------------- -->
  <!-- <br />
  <h1>EVENTOS</h1>
  <button @click="handleClick('Texto')">Actívame</button>
  <button @click="handleClick('Left')">Click left</button>
  <button @click.middle="handleClick('Middle')">Click middle</button>
  <button @click.right="handleClick('Right')">Click right</button>
  <br /> -->
  ---------------------------------------------------------------
  <div class="container text-center mt-3">
    <h1>Reactividad</h1>
    <h2 :class="classCounter">
      {{ counter }}
    </h2>
    <div class="btn-group mb-3">
      <button @click="handleCounter('increment')" class="btn btn-success">
        Incrementa
      </button>
      <button @click="handleCounter('decrement')" class="btn btn-danger">
        Decrementa
      </button>
      <button @click="handleCounter('reset')" class="btn btn-secondary">
        Resetea
      </button>
      <button @click="add" :disabled="bloqAddBtn" class="btn btn-primary">
        Add
      </button>
    </div>
    <ul class="list-group">
      Mis favoritos
      <li
        class="list-group-item"
        v-for="(item, index) in arrayFavorites"
        :key="index"
      >
        {{ item }}
      </li>
    </ul>
  </div>
</template>

<style>
.zero {
  color: black;
}
.positive {
  color: green;
}
.negative {
  color: red;
}
</style>
