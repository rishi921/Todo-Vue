<template>
    <div>
      <h1>Product List</h1>

      <div v-if="loading">Loading...</div>

      <div v-if="error" class="error">{{ error.message }}</div>

      <table table table-bordered v-if="!loading && !error" class="table table-bordered table-striped">
        <thead>
          <tr>
            <th>Title</th>
            <th>Price</th>
            <th>Category</th>
            <th>Description</th>
            <th>Rating</th>
            <th>Actions</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="product in products" :key="product.id">
            <td>{{ product.title }}</td>
            <td>{{ product.price }}</td>
            <td>{{ product.category }}</td>
            <td>{{ product.description }}</td>
            <td>{{ product.rating.rate }} ({{ product.rating.count }} reviews)</td>
            <td>
              <button @click="viewDetails(product)" class="btn btn-info">View Details</button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  
  export default {
    name: 'ProductList',
    data() {
      return {
        products: [],
        loading: false,
        error: null,
      };
    },
    created() {
      this.fetchProducts();
    },
    methods: {
      fetchProducts() {
        this.loading = true;
        this.error = null;
  
        axios
          .get('https://fakestoreapi.com/products')
          .then(response => {
            this.products = response.data;
            this.loading = false;
          })
          .catch(error => {
            this.error = error;
            this.loading = false;
          });
      },
      viewDetails(product) {
   
        this.$emit('view-details', product);
      }
    }
  };
  </script>
  
  <style scoped>
  .error {
    color: red;
  }
  
  .table {
    width: 100%;
    margin-top: 20px;
    text-align: left;
  }
  
  th, td {
    padding: 10px;
  }
  </style>