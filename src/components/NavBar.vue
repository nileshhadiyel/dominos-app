<template>
  <div class="navbar">
    <div class="logo" @click="redirectToOrders">
      <img src="../static/assets/logo_white.svg" alt="Dominos Logo" />
    </div>
    <div class="nav-links">
      <router-link to="/orders">Orders</router-link>
      <router-link to="/order-online">Order Online</router-link>
      <router-link to="/beverages">Beverages</router-link>
      <router-link to="/desserts">Desserts</router-link>
    </div>
  </div>
</template>

<script setup>
import { useRouter } from "vue-router";

const redirectToOrders = () => {
  useRouter.push("/orders");
};
</script>

<style scoped>
.navbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 10px 20px;
  background-color: #006491;
  color: white;
}

.logo {
  cursor: pointer;
}

.logo img {
  max-height: 40px;
}

.nav-links {
  display: flex;
  gap: 20px;
}

.router-link-active {
  font-weight: bold;
}
</style>
