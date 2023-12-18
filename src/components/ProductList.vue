<template>
    <div class="product-list">
      <h1>Список товаров</h1>
      <PostButton @postNewElement="postNewElement"></PostButton>
      <ul>
        <ProductElement @editClicked="editClicked" @deleteClicked="deleteClicked" v-for="product in sortedList" :key="product.id" :product="product"></ProductElement>
      </ul>
    </div>
  </template>
  
  <script>
  import axiosConfig from '@/axiosConfig';
  import ProductElement from './ProductElement.vue';
  import PostButton from './PostButton.vue';
  export default {
    name: 'ProductList',
    props:{
      sortNumber:{
        type:Number
      }
    },
    data() {
        return {
            products: [],
            sortedList:[]
        };
    },
    created() {
        this.fetchData();
    },
    methods: {
        fetchData() {
            axiosConfig.get('/products/all')
                .then(response => {
                this.products = response.data;
                this.sortList(this.sortNumber);
            })
                .catch(error => {
                console.error('Ошибка при загрузке данных:', error);
            });
        },
        editClicked(product){
          this.$emit('editContent',product);
        },
        deleteClicked(product){
          this.$emit('deleteContent',product);
        },
        postNewElement(){
          this.$emit('postNewElement')
        },
        sortList(sortNumber){
          switch (sortNumber) {
            case 1:
              this.sortedList= this.products.slice().sort((a,b)=>{
              return a['price']-b['price'];
              })
              break;
            case 2:
              this.sortedList= this.products.slice().sort((a,b)=>{
              return new Date(a.production_date).setHours(0,0,0,0)-new Date(b.production_date).setHours(0,0,0,0);
              })
              break;
            case 3:
              this.sortedList= this.products.slice().sort((a,b)=>{
              return new Date(a.expiration_date).setHours(0,0,0,0)-new Date(b.expiration_date).setHours(0,0,0,0);
              })
              break;
          
            default:
              this.sortedList= this.products.slice();
              break;
          }
        }
    },
    components: { ProductElement, PostButton }
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