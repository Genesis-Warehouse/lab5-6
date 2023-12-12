<template>
    <li>
        <span class="batch-number">Номер:{{ batch.number }}</span>
        <span class="batch-date">Дата: {{ batch.date }}</span>
        <span><img @click="editBatch" src="../icons/icon_edit.png" alt="edit"><img @click="deleteBatch" src="../icons/icon_delete.png" alt="delete"></span>
      </li>
</template>

<script>
    export default{
        name:'BatchElement',
        props:{
            batch:{
                type:Object
            }
        },
        data(){
            return{
                batchData:{}
            }
        },
        created(){
            this.batchData=this.batch;
        },
        methods:{
            editBatch(){
                this.$emit('editClicked',this.batchData);
            },
            deleteBatch(){
                this.$emit('deleteClicked',this.batchData);
            }

        }
        
    }
</script>

<style scoped>
img{
    width: 20px;
    height: 20px;
    padding: 5px;
    margin: 0 5px 0 5px;
}
img:hover{
    background-color: #164B70;
    border-radius: 15%;
    cursor: pointer;
}
</style>