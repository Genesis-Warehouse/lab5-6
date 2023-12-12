<template>
    <div class="category-list">
      <h2 class="category-list-title">Категории</h2>
      <ul class="category-list-items">
        <li @click="selected1" :class="{'is-selected':selectedCategory===1}" class="category-list-item">
          Продукты      
        </li>
        <li @click="selected2" :class="{'is-selected':selectedCategory===2}" class="category-list-item">
          Партии
        </li>
        <li @click="selected3" :class="{'is-selected':selectedCategory===3}" class="category-list-item">
          Разделы склада
        </li>
      </ul>
    </div>
  </template>
  
  <script>
  export default {
    name: 'CategoryList',
    data(){
      return{
        selectedCategory:0
      }
    },
    methods:{
      selected1(){
        this.selectedCategory=1;
        this.$emit('update-selected-category',1);
      },
      selected2(){
        this.selectedCategory=2;
        this.$emit('update-selected-category',2);
      },
      selected3(){
        this.selectedCategory=3;
        this.$emit('update-selected-category',3);
      }
    },
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
  .is-selected{
    background-color: #41B882;
    color: #35495e;
  }
  </style>