<template>
    <div class="test">
        <div  class="field"></div>
        <div v-on:click="onClickedButton" class="test_button">click me!</div>
    </div>
</template>

<script>
import axios from 'axios';

 export default {
    name: 'TestLala',
    // props: {
    //   categories: {
    //     type: Array,
    //     required: true
    //   }
    // },
    methods: {
      onClickedButton() {
        axios.get('http://localhost:8000/products/all').then(response =>(console.log(response)));
        // Проверяем get запрос
      }
    }
  }
</script>

<style scoped>
.test_button{
    width: 300px;
    height: 100px;
    border: 1px solid #000;
    border-radius: 5px;
    background-color: red;
}
</style>