<template>
  <div>
    <NavBar />
    <!-- <SideBar /> -->
<div class="justify-between">
   <PizzaCard />
    <CheckOut />  
</div>
   
  </div>
</template>

<script>
import NavBar from "./components/NavBar.vue";
// import SideBar from "./components/SideBar.vue";
import PizzaCard from "./components/PizzaCard.vue";
import CheckOut from "./components/CheckOut.vue";

export default {
  name: "App",
  components: {
    NavBar,
    // SideBar,
    PizzaCard,
    CheckOut,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
}
</style>
