<template>
  <div class="pizza-card">
    <div class="image-area">
      <img :src="pizza.image" alt="Pizza" class="pizza-image" />
    </div>
    <div class="details-area">
      <h2 class="pizza-name">{{ pizza.name }}</h2>
      <p class="pizza-description">{{ pizza.description }}</p>
      <div class="divider"></div>
      <div class="size-crust-selection">
        <div class="size">
          <label for="size">Size:</label>
          <select v-model="selectedSize" id="size">
            <option v-for="size in pizza.sizes" :key="size.value" :value="size.value">
              {{ size.label }} - {{ size.price }}
            </option>
          </select>
        </div>
        <div class="crust">
          <label for="crust">Crust:</label>
          <select v-model="selectedCrust" id="crust">
            <option v-for="crust in pizza.crusts" :key="crust.value" :value="crust.value">
              {{ crust.label }} - {{ crust.price }}
            </option>
          </select>
        </div>
      </div>
      <div class="actions">
        <button class="delete-button" @click="deletePizza" :disabled="pizzaCounter === 0">
          <i class="material-icons">delete</i>
        </button>
        <span class="counter">{{ pizzaCounter }}</span>
        <button class="add-button" @click="addPizza">
          <i class="material-icons">add</i>
        </button>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";

const pizza = {
  name: "Pepperoni Pizza",
  description: "Delicious pepperoni pizza with a blend of cheeses.",
  image: "../static/Images/Pizzas/peppy_paneer.jpg",
  sizes: [
    { label: "Regular", value: "regular", price: "$10" },
    { label: "Medium", value: "medium", price: "$12" },
    { label: "Large", value: "large", price: "$15" },
  ],
  crusts: [
    { label: "Hand Tossed", value: "hand_tossed", price: "$0" },
    { label: "Cheese Burst", value: "cheese_burst", price: "$2" },
    { label: "Pan Pizza", value: "pan_pizza", price: "$1" },
    { label: "Thin Crust", value: " thin_crust", price: "$0" },
  ],
};

const selectedSize = ref(pizza.sizes[0].value);
const selectedCrust = ref(pizza.crusts[0].value);
const pizzaCounter = ref(0);

const deletePizza = () => {
  if (pizzaCounter.value > 0) {
    pizzaCounter.value--;
  }
};

const addPizza = () => {
  pizzaCounter.value++;
};
</script>

<style scoped>
.pizza-card {
  display: flex;
  border: 1px solid #ddd;
  padding: 10px;
  margin: 10px;
  max-width: 400px;
}

.image-area {
  width: 40%;
}

.pizza-image {
  max-width: 100%;
  height: auto;
}

.details-area {
  width: 60%;
  padding: 10px;
  display: flex;
  flex-direction: column;
}

.size-crust-selection {
  margin-top: 10px;
  display: flex;
  align-items: center;
}

.size,
.crust {
  flex: 1;
  display: flex;
  align-items: center;
}

.size label,
.crust label {
  margin-right: 8px;
}

.actions {
  margin-top: 10px;
  display: flex;
  align-items: center;
}

.delete-button,
.add-button {
  border: none;
  background: none;
  cursor: pointer;
  font-size: 20px;
  margin: 0 10px;
}

.counter {
  font-size: 18px;
}

.delete-button:disabled {
  color: #ccc;
  cursor: not-allowed;
}

@media screen and (max-width: 600px) {
  .pizza-card {
    flex-direction: column;
  }

  .image-area {
    width: 100%;
  }

  .details-area {
    width: 100%;
    padding-top: 10px;
  }

  .size-crust-selection {
    flex-direction: column;
    align-items: flex-start;
    margin-top: 15px;
  }

  .size,
  .crust {
    width: 100%;
    margin-bottom: 10px;
  }

  .delete-button,
  .add-button {
    margin: 10px 0;
  }

  .counter {
    margin: 0 10px;
  }
}
</style>
