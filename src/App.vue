<template>
  <div id="app">
    <ProductDisplay msg="Welcome to Your Vue.js App" />
  </div>
</template>

<script>
import ProductDisplay from "./components/ProductDisplay.vue";

export default {
  name: "App",
  components: {
    ProductDisplay,
  },
};
</script>
