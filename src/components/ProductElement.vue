<template>
    <li>
        <span class="product-name">{{ product.name }}</span>
        <span class="product-price">{{ product.price }} руб.</span>
        <span class="product-production_date">Выпущен: {{ product.production_date }}</span>
        <span class="product-expiration_date">Годен до:{{ product.expiration_date }} руб.</span>
        <span><img @click="editProduct" src="../icons/icon_edit.png" alt="edit"><img @click="deleteProduct" src="../icons/icon_delete.png" alt="delete"></span>
    </li>
</template>

<script>
    export default{
        name:'ProductElement',
        props:{
            product:{
                type:Object
            }
        },
        data(){
            return{
                productData:{}
            }
        },
        created(){
            this.productData=this.product;
        },
        methods:{
            editProduct(){
                this.$emit('editClicked',this.productData);
            },
            deleteProduct(){
                this.$emit('deleteClicked',this.productData);
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
    transition: background-color 0.3s, color 0.3s;
    border-radius: 15%;
}
img:hover{
    background-color: #164B70;
    cursor: pointer;
}
.product-name{
    width: 200px;
}
</style>