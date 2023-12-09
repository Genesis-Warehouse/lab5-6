<template>
    <div class="product-list">
      <h1>Разделы склада</h1>
      <ul>
        <li v-for="section in sections" :key="section.id">
          <span class="section-name">{{ section.name }}</span>
        </li>
      </ul>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  
  export default {
    name: 'WarehouseSections',
    data() {
      return {
        sections: [],
      };
    },
    created() {
      this.fetchData();
    },
    methods: {
      fetchData() {
        axios.get('http://localhost:8000/warehouse_sections/all')
          .then(response => {
            this.sections = response.data;
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
  
  .section-name {
    font-weight: bold;
  }
  </style>