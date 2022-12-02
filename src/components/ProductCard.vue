<template>
  <div class="wrapper">
    <figure class="image-wrapper">
      <img alt="product" v-bind:src="product.image" />
    </figure>
    <div class="description-wrapper">
      <h1
        class="title"
        :class="
          product.category === 'men\'s clothing'
            ? 'text-men'
            : product.category === 'women\'s clothing'
            ? 'text-women'
            : ''
        "
      >
        {{ product.title }}
      </h1>

      <div class="category-rating-wrapper">
        <span>{{ product.category }}</span>
        <div class="rating-wrapper">
          <span>{{ product.rating.rate }}/5</span>
          <div class="rating">
            <span
              :class="
                product.category === 'men\'s clothing'
                  ? 'dot-outlined-men dot-filled-men'
                  : product.category === 'women\'s clothing'
                  ? 'dot-outlined-women dot-filled-women'
                  : ''
              "
              v-for="n in Math.ceil(product.rating.rate)"
              :key="n"
            ></span>
            <span
              :class="
                product.category === 'men\'s clothing'
                  ? 'dot-outlined-men'
                  : product.category === 'women\'s clothing'
                  ? 'dot-outlined-women'
                  : ''
              "
              v-for="n in maxRating - Math.ceil(product.rating.rate)"
              :key="n"
            ></span>
          </div>
        </div>
      </div>

      <div class="description">
        <p>
          {{ product.description }}
        </p>
      </div>

      <div class="price-actions-wrapper">
        <h2
          class="price"
          :class="
            product.category === 'men\'s clothing'
              ? 'text-men'
              : product.category === 'women\'s clothing'
              ? 'text-women'
              : ''
          "
        >
          ${{ product.price }}
        </h2>
        <div class="actions">
          <button
            :class="
              product.category === 'men\'s clothing'
                ? 'button-filled-men'
                : product.category === 'women\'s clothing'
                ? 'button-filled-women'
                : ''
            "
          >
            Buy now</button
          ><button
            :class="
              product.category === 'men\'s clothing'
                ? 'button-outlined-men'
                : product.category === 'women\'s clothing'
                ? 'button-outlined-women'
                : ''
            "
            @click="nextProduct"
          >
            Next product
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ProductCard",
  props: {
    product: { type: Object },
    nextProduct: { type: Function },
  },
  data() {
    return {
      maxRating: 5,
    };
  },
};
</script>
