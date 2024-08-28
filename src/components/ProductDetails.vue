<template>
  <div>
    <h1>Product Details</h1>

    <div v-if="product">
      <h2>{{ product.title }}</h2>
      <p><strong>Price:</strong> {{ product.price }}</p>
      <p><strong>Category:</strong> {{ product.category }}</p>
      <p><strong>Description:</strong> {{ product.description }}</p>
      <p>
        <strong>Rating:</strong> {{ product.rating.rate }} ({{
          product.rating.count
        }}
        reviews)
      </p>
      <button @click="goBack" class="btn btn-secondary">Back to List</button>
    </div>

    <div v-if="!product" class="error">No product details available.</div>
  </div>
</template>

<script>
export default {
  name: "ProductDetails",
  props: {
    product: {
      type: Object,
      required: true,
    },
  },
  methods: {
    goBack() {
      this.$emit("go-list");
    },
  },
};
</script>

<style scoped>
.error {
  color: red;
}
</style>
