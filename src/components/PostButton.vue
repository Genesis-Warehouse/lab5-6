<template>
<li>
    <div @click="postNewElement" class="post_button">
    <span>Добавить новую запись</span>
    <img src="../icons/icon_post.png" alt="post">
    </div>
</li>
</template>

<script>
    export default{
        name:'PostButton',
        methods:{
            postNewElement(){
                this.$emit('postNewElement');
            }
        }
    }
</script>

<style scoped>
.post_button {
    display: flex;
    align-items: center;
    justify-content: center;
    background-color: #8FB8D6;
    color: #164B70;
    padding: 10px;
    border-radius: 4px;
    transition: background-color 0.3s, color 0.3s;
  }
  
  .post_button span {
    margin-right: 10px;
  }
  .post_button:hover{
    background-color: #164B70;
    color: #8FB8D6;
    cursor: pointer;
  }
</style>