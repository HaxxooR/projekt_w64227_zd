<template>
    <div class="product-grid pa-16 ">
      <div v-for="(item, index) in items" :key="index" class="product-card">
        <h3>{{ item.id }}. {{ item.product_name }}</h3>
        <p>{{ item.short_description }}</p>
        <p>Cena: {{ item.product_price }}</p>
        <p>Opis: {{ item.long_description }}</p>
        <p>Kategoria: {{ item.product_category }}</p>
        <p>Dostępność: {{ item.product_status }}</p>
        <v-btn size="x-large">Zobacz</v-btn>
        <hr />
      </div>
    </div>
  </template>
  
  <style>
  .product-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-gap: 20px;
  }
  
  .product-card {
    border: 1px solid #ccc;
    border-radius: 4px;
    padding: 10px;
  }
  
  .product-card h3 {
    margin-top: 10px;
  }
  </style>
  
  <script>
  import axios from 'axios';
  
  export default {
    data() {
      return {
        items: [],
      };
    },
    mounted() {
      this.fetchData();
    },
    methods: {
      fetchData() {
        axios
          .get('http://127.0.0.1:8000/api/products')
          .then(response => {
            this.items = response.data;
          })
          .catch(error => {
            console.error(error);
          });
      },
    },
  };
  </script>
  
  