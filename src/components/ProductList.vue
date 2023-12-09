<template>
    <div class="product-list">
      <h1>Список товаров</h1>
      <ul>
        <li v-for="product in products" :key="product.id">
          <span class="product-name">{{ product.name }}</span>
          <span class="product-price">{{ product.price }} руб.</span>
        </li>
      </ul>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  
  export default {
    name: 'ProductList',
    data() {
      return {
        products: [],
      };
    },
    created() {
      this.fetchData();
    },
    methods: {
      fetchData() {
        axios.get('http://localhost:8000/products/all')
          .then(response => {
            this.products = response.data;
          })
          .catch(error => {
            console.error('Ошибка при загрузке данных:', error);
          });
      },
    },
  };
  </script>
  
  <style scoped>
  .product-list {
    font-family: 'Arial', sans-serif;
    background-color: #8FB8D6;
    padding: 20px;
    border-radius: 10px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
  }
  
  h1 {
    color: #164B70;
  }
  
  ul {
    list-style-type: none;
    padding: 0;
  }
  
  li {
    background-color: #75AED6;
    color: #164B70;
    margin: 10px 0;
    padding: 10px;
    border-radius: 5px;
    display: flex;
    justify-content: space-between;
  }
  
  .product-name {
    font-weight: bold;
  }
  
  .product-price {
    font-style: italic;
  }
  </style>