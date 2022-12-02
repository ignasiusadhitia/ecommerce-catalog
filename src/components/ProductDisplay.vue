<template>
  <div class="container">
    <div
      class="background"
      :class="
        product.category === 'men\'s clothing'
          ? 'background-men'
          : product.category === 'women\'s clothing'
          ? 'background-women'
          : ''
      "
    ></div>
    <div v-if="isLoading" class="outer-wrapper">
      <ProductLoadingCard />
    </div>
    <div
      class="outer-wrapper"
      v-else-if="
        product.category === 'men\'s clothing' ||
        product.category === 'women\'s clothing'
      "
    >
      <ProductCard :product="product" :nextProduct="nextProduct" />
    </div>
    <div class="outer-wrapper" v-else>
      <ProductUnavailableCard :nextProduct="nextProduct" />
    </div>
  </div>
</template>

<script>
import ProductLoadingCard from "./ProductLoadingCard.vue";
import ProductCard from "./ProductCard.vue";
import ProductUnavailableCard from "./ProductUnavailableCard.vue";

export default {
  name: "ProductDisplay",
  components: {
    ProductLoadingCard,
    ProductCard,
    ProductUnavailableCard,
  },
  data() {
    return {
      index: 1,
      product: {},
      isLoading: false,
    };
  },
  methods: {
    async getData(index) {
      this.isLoading = true;
      const res = await fetch(`https://fakestoreapi.com/products/${index}`);
      const finalRes = await res.json();
      this.product = finalRes;
      this.isLoading = false;
    },
    nextProduct() {
      if (this.index === 20) {
        this.index = 1;
      } else {
        this.index = this.index + 1;
      }

      this.getData(this.index);
    },
  },
  mounted() {
    this.getData(this.index);
  },
};
</script>
