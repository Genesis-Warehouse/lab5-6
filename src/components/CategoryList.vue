<template>
    <div class="category-list">
      <h2 class="category-list-title">Категории</h2>
      <ul class="category-list-items">
        <li v-for="category in categories" :key="category.id" class="category-list-item">
          {{ category.name }}
        </li>
      </ul>
    </div>
  </template>
  
  <script>
  export default {
    name: 'CategoryList',
    props: {
      categories: {
        type: Array,
        required: true
      }
    }
  }
  </script>
  
  <style scoped>
  .category-list {
    background-color: #35495e;
    padding: 15px;
    border-radius: 5px;
    height: 100%;
  }
  
  .category-list-title {
    color: #41B882;
    font-size: 1.5em;
    margin-bottom: 10px;
  }
  
  .category-list-items {
    list-style: none;
    padding: 0;
    margin: 0;
  }
  
  .category-list-item {
    color: #41B882;
    padding: 8px;
    margin-bottom: 5px;
    border-radius: 3px;
    cursor: pointer;
    transition: background-color 0.3s;
  }
  
  .category-list-item:hover {
    background-color: #41B882;
    color: #35495e;
  }
  </style>