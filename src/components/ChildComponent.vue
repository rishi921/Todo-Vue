<template>
  <div>
    <h1>Child Component</h1>
    <h2>Received from parent: {{ message }}</h2>
    <input v-model="childInput" placeholder="Type a message to the parent" />
    <button @click="sendMessageToParent">Send to Parent</button>
  </div>
</template>

<script>
export default {
  name: "ChildComponent",
  props: {
    message: {
      type: String,
      required: true,
    },
  },
  data() {
    return {
      childInput: "",
    };
  },
  methods: {
    sendMessageToParent() {
      this.$emit("update-message", this.childInput);
      this.childInput = "";
    },
  },
};
</script>
