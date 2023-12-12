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
    padding: 10px;
    border-radius: 4px;
  }
  
  .post_button span {
    margin-right: 10px;
    color: #164B70;
  }
</style>