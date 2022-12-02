<template>
  <div class="wrapper">
    <div class="message-wrapper">
      <p>This product is unavailable to show</p>
      <button @click="nextProduct">Next Product</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "ProductUnavailableCard",
  props: {
    nextProduct: { type: Function },
  },
};
</script>

<style scoped>
.wrapper {
  background: var(--white) url("../assets/images/sad-face.svg") no-repeat center;
  background-size: 55%;
}

.message-wrapper {
  width: 100%;
  min-height: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
</style>
