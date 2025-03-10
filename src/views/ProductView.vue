<template lang="">
    <NavBar :name=userName :role="roleId" />
    <div class ="container">
        <h2 class="my-5">product list</h2>

        <a href="/product-add" class="btn btn-success mb-5">Add Product</a>

        <table class="table table-striped">
            <thead>
                <tr>
                    <th>#</th>
                    <th>Name</th>
                    <th>Price</th>
                    <th>Image</th>
                    <th>Action</th>
                </tr>
                
            </thead>
            <tbody>
                <tr v-for="(item, index) in items" :key="index">
                    <td>{{ index+1}}</td>
                    <td>{{item.name}}</td>
                    <td>{{item.price}}</td>
                    <td><img :src="url+item.image" class="object-fit-cover" style="width:100px; height:100px" ></td>
                    <td><RouterLink :to="{name:'productUpdate', params:{ productId: item.id}}">edit</RouterLink></td>
                </tr>
            </tbody>
        </table>
        
    </div>
</template>
<script>
import NavBar from '@/components/NavBar.vue'
import router from '@/router'
import axios from 'axios'

export default {
    components:{
         NavBar
        },
  data() {
    return {
      userName: '',
      roleId :'',
      items: [],
      url:'http://localhost/web_order_food/be_order_food/storage/app/public/items/'
    }
  },
    mounted(){
        this.userName = localStorage.getItem('name')
        this.roleId = localStorage.getItem('role_id')
        if (!this.userName || this.userName == '' || this.userName ==null){
        router.push({ name: 'login'})
        }
        if(this.roleId != 4) {
        router.push({ name: 'home'})
        }
        this.getItems()
    },
    methods: {
        getItems() {
            axios.get('http://127.0.0.1:8000/api/item', {
               headers: {
                "Authorization" : `Bearer ${localStorage.getItem('token')}`
              }
            })
            .then((response) => {
              this.items= response.data.data

            })
            .catch(function (error) {
                console.log(error);
                console.log('lỗi khi đăng nhập');
            });
        }
    }
        
}
</script>
<style lang="">
    
</style>