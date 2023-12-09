<template>
    <div>
      <div v-if="selectedCategory === 1">
        <ProductList />
      </div>
      <div v-else-if="selectedCategory === 2">
        <BatchesList />
      </div>
      <div v-else-if="selectedCategory === 3">
        <WarehouseSections />
      </div>
      <div v-else>
        <p>Добро пожаловать! Выберите интересующую вас категорию.</p>
      </div>
    </div>
  </template>
  
  <script>
  import ProductList from './ProductList.vue';
  import BatchesList from './BatchesList.vue';
  import WarehouseSections from './WarehouseSections.vue';
  
  export default {
    name:'ContentList',
    props: {
      selectedCategory: {
        type: Number,
        required: true,
        validator: value => value >= 1 && value <= 3,
      },
    },
    components: {
      ProductList,
      BatchesList,
      WarehouseSections,
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