<template>
  <div class="pizza-card">
    <img :src="pizza.image" alt="Pizza" class="pizza-image" />
    <div class="pizza-details">
      <h2>{{ pizza.name }}</h2>
      <p class="pizza-price">{{ pizza.price }} USD</p>
      <div class="quantity-controls">
        <button @click="decrementQuantity">-</button>
        <p>{{ quantity }}</p>
        <button @click="incrementQuantity">+</button>
      </div>
    </div>
    <button class="delete-button" @click="removePizza">Delete</button>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const pizza = {
  name: 'Margherita Pizza',
  price: 10.99,
  image: 'https://example.com/pizza-margherita.jpg',
};

const quantity = ref(1);

const decrementQuantity = () => {
  if (quantity.value > 1) {
    quantity.value--;
  }
};

const incrementQuantity = () => {
  quantity.value++;
};

const removePizza = () => {
};

</script>

<style>
.pizza-card {
  display: flex;
  align-items: center;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 8px;
  margin-bottom: 10px;
}

.pizza-image {
  width: 100px;
  height: 100px;
  object-fit: cover;
  margin-right: 10px;
}

.pizza-details {
  flex: 1;
}

.pizza-price {
  font-weight: bold;
  margin-bottom: 5px;
}

.quantity-controls {
  display: flex;
  align-items: center;
}

.quantity-controls button {
  padding: 5px 10px;
  border: none;
  background-color: #eee;
  cursor: pointer;
  margin: 0 5px;
}

.delete-button {
  background-color: red;
  color: white;
  border: none;
  padding: 5px 10px;
  border-radius: 5px;
  cursor: pointer;
}

</style>
