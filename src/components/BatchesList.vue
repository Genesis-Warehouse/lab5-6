<template>
    <div class="product-list">
      <h1>Список партий</h1>
      <ul>
        <li v-for="batch in batches" :key="batch.id">
          <span class="batch-number">Номер:{{ batch.number }}</span>
          <span class="batch-date">Дата: {{ batch.date }}</span>
        </li>
      </ul>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  
  export default {
    name: 'BatchesList',
    data() {
      return {
        batches: [],
      };
    },
    created() {
      this.fetchData();
    },
    methods: {
      fetchData() {
        axios.get('http://localhost:8000/batches/all')
          .then(response => {
            this.batches = response.data;
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
  
  .batch-number {
    font-weight: bold;
  }
  
  .batch-date {
    font-style: italic;
  }
  </style>