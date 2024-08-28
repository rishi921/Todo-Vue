<template>
  <div>
    <!-- <h1>Parent Component</h1> -->
    <!-- <h2>Message from Parent to Child: {{ parentMessage }}</h2>
    <h2>Message from Child: {{ childMessage }}</h2>
    <ChildComponent
    :message="parentMessage"
    @update-message="handleUpdateMessage"
    /> -->

    <h1>Product Details</h1>
    <button @click="$emit('go-list')">Back to Product List</button>
    <div v-if="product">
      <h2>{{ product.title }}</h2>
      <h3>Rs. {{ product.price }}</h3>
      <image
        alt=" product.title"
        src="product.image"
        style="width: 200px; height: auto"
      />
      <p>
        <strong>{{ product.description }}</strong
        >strong>
      </p>
      <h4>Category: {{ product.category }}</h4>
    </div>

    <div v-else><p>Loading product details ....</p></div>
  </div>
</template>

<script>
import ChildComponent from "./ChildComponent.vue";

import axios from "axios";
export default {
  name: "ParentComponent",
  components: {
    ChildComponent,
  },
  data() {
    return {
      parentMessage: "Hello from Parent",
      childMessage: "",
    };
  },
  methods: {
    handleUpdateMessage(newMessage) {
      this.childMessage = newMessage;
    },
  },
};
</script>
