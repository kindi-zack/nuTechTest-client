<template>
    <div>
        <div class="clearfix mb-3"> 
            <button @click.prevent="logout" class="float-end badge  bg-dark">Logout</button>
        </div>

        <AddProduct :baseUrl="baseUrl" :fetchProduct='fetchProduct' :showForm='showForm' v-if="!product"></AddProduct>
        
        <div v-if="product" class="clearfix mb-3"> 
            <button @click.prevent="showForm(false)" class="float-end badge  bg-primary">Tambah Product</button>
        </div>


        <div v-if="product" class="container-fluid bg-trasparent my-4 p-3" style="position: relative;">
            <div class="row row-cols-1 row-cols-xs-2 row-cols-sm-2 row-cols-lg-4 g-3">
                <Product v-for="item in items" :key="item.id" :item='item'></Product>
            </div>
        </div>

    </div>
</template>

<script>
import axios from 'axios'
import AddProduct from '../component/AddProduct.vue'
import Product from '../component/Product.vue'
export default {
    props: ['changeIsLogin', 'baseUrl'],
    data(){
        return {
           items : [],
           product: true,
        }
    },
    components: {
        AddProduct,
        Product
    },
    methods: {
        showForm(value){
            this.product = value
        },
       
        fetchProduct(value){
            axios({
                method: 'GET',
                url: `${this.baseUrl}barang`,
            })
            .then(({data})=>{
                if (data.length === 0) this.product = false
                console.log(data)
                this.items = data
            
            })
            .catch(({response})=>{
                console.log(response)
            })
        },
        logout(){
            localStorage.removeItem('access_token')
            this.changeIsLogin(false)
          
        }
    },
    created(){
        this.fetchProduct()
    }
}
</script>

<style>

</style>

