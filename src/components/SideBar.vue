<template>
  <div class="sidebar">
    <div class="menu-icon" @click="toggleSidebar">
      <img src="/path/to/menu-icon.png" alt="Menu Icon" />
    </div>
    <div class="sidebar-content" :class="{ active: isOpen }">
      <div class="close-icon" @click="toggleSidebar">
        <link
          href="https://fonts.googleapis.com/icon?family=Material+Icons"
          rel="stylesheet"
        />
      </div>
      <div class="options">
        <div class="option">My Orders</div>
        <div class="option">Cart</div>
        <div class="option">Payments</div>
        <div class="option">Status</div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";

const isOpen = ref(false);

const toggleSidebar = () => {
  isOpen.value = !isOpen.value;
};
</script>

<style scoped>
.sidebar {
  position: fixed;
  top: 0;
  left: -300px; /* Initial position, hidden */
  width: 300px;
  height: 100%;
  background-color: #333;
  color: white;
  transition: left 0.3s ease-in-out;
}

.sidebar-content {
  position: absolute;
  width: 100%;
  height: 100%;
  background-color: #333;
  padding: 20px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.sidebar-content.active {
  left: 0;
}

.menu-icon,
.close-icon {
  cursor: pointer;
}

.options {
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.option {
  padding: 10px;
  border-bottom: 1px solid #555;
  cursor: pointer;
}

.option:last-child {
  border-bottom: none;
}
</style>
