<template>
    <div class="product-list">
      <h1>Список партий</h1>
      <PostButton @postNewElement="postNewElement"></PostButton>
      <ul>
        <BatchElement @editClicked="editClicked" @deleteClicked="deleteClicked" v-for="batch in batches" :key="batch.id" :batch="batch"></BatchElement>
      </ul>
    </div>
  </template>
  
  <script>
  import PostButton from './PostButton.vue';
  import axiosConfig from '@/axiosConfig';
  import BatchElement from './BatchElement.vue';
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
            axiosConfig.get('/batches/all')
                .then(response => {
                this.batches = response.data;
            })
                .catch(error => {
                console.error('Ошибка при загрузке данных:', error);
            });
        },
        editClicked(batch){
          this.$emit('editContent',batch);
        },
        deleteClicked(batch){
          this.$emit('deleteContent',batch);
        },
        postNewElement(){
          this.$emit('postNewElement')
        }
    },
    components: { BatchElement, PostButton }
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