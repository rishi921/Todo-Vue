<template>
  <div id="app">
    <h1>Fake Store</h1>
    <!-- <h1 class="bg-primary text-white text-center m-2 p-2">
      {{ name }}'s' Todo List
    </h1> -->
    <!-- Use ParentComponent -->
    <ParentComponent />
    <ProductList />
    <ProductDetails />
    <Home />
    <!-- Uncomment if you want to use Todo component -->
    <!-- <Todo /> -->
  </div>
</template>

<script>
import ParentComponent from "./components/ParentComponent.vue";
import ProductList from "./components/ProductList.vue";
import ProductDetails from './components/ProductDetails.vue';
import Home from "./components/Home.vue";
// import Todo from "./components/Todo.vue";

export default {
  name: "App",
  components: {
    ParentComponent, // Register ParentComponent here
    // Todo, // Register Todo component if you plan to use it
    ProductList
  },
  data() {
    return {
      name: "Rishi",
    };
  },
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
