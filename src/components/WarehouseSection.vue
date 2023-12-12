<template>
    <li>
        <span class="section-name">{{ section.name }}</span>
        <span><img @click="editSection" src="../icons/icon_edit.png" alt="edit"><img @click="deleteSection" src="../icons/icon_delete.png" alt="delete"></span>
    </li>
  
</template>

<script>
    export default{
        name:'SectionElement',
        props:{
            section:{
                type:Object
            }
        },
        data(){
            return{
                sectionData:{}
            }
        },
        created(){
            this.sectionData=this.section;
        },
        methods:{
            editSection(){
                this.$emit('editClicked',this.sectionData);
            },
            deleteSection(){
                this.$emit('deleteClicked',this.sectionData);                
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