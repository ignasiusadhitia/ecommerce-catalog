<template>
  <div class="wrapper loading">
    <div class="image-wrapper"></div>
    <div class="description-wrapper">
      <div class="title"></div>

      <div class="category-rating-wrapper"></div>

      <div class="description"></div>

      <div class="price-actions-wrapper"></div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ProductLoadingCard",
};
</script>

<style scoped>
.title {
  min-height: 4rem;
}

.category-rating-wrapper {
  min-height: 1.5rem;
}

.description {
  margin-bottom: 15px;
  border: none;
}

.price-actions-wrapper {
  min-height: 6rem;
}

.loading .image-wrapper,
.loading .title,
.loading .category-rating-wrapper,
.loading .description,
.loading .price-actions-wrapper {
  background-color: var(--gainsboro);
  background: linear-gradient(
      100deg,
      rgba(255, 255, 255, 0) 40%,
      rgba(255, 255, 255, 0.5) 50%,
      rgba(255, 255, 255, 0) 60%
    )
    var(--gainsboro);
  background-size: 200% 100%;
  background-position-x: 180%;
  animation: 1s loading ease-in-out infinite;
}

@keyframes loading {
  to {
    background-position-x: -20%;
  }
}
</style>
