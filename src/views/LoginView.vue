<template lang="">
    <div class="container">
        <div class="row vh-100 justify-content-center align-items-center login-container">
            <div class="col-md-4">
                <div class="card mt-5 shadow">
                    <div class="card-body">
                        <h3 class="card-body">Đăng nhập</h3>
                        <form @submit.prevent>
                            <div class="form-group mb-3">
                                <label for="email" class="form-label">Email</label>
                                <input type="email" v-model="email" class="form-control" id="email" name="email" required>
                            </div>
                            <div class="form-group mb-3">
                                <label for="password" class="form-label">Mật khẩu</label>
                                <input type="password" v-model="password" class="form-control" id="password" name="password" required>
                            </div>
                            <button @click="login()" class="btn btn-primary btn-block form-control">Đăng nhập</button>
                        </form>
                        <div class="text-center mt-3">
                            <a href="#">Quên mật khẩu?</a>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>

</template>
<script>
import axios from 'axios';
import router from '@/router';

export default {
    data(){
        return {
            email: "",
            password: ""
        }
    },
    methods: {
        login(){
            axios.post('http://127.0.0.1:8000/api/auth/login', {
                email: this.email,
                password: this.password
            })
            .then(function (response) {
                console.log(response);
                localStorage.setItem('email', response.data.data.email)
                localStorage.setItem('name', response.data.data.name)
                localStorage.setItem('role_id', response.data.data.role_id)
                localStorage.setItem('token', response.data.data.token)
                router.push({name : 'home' })
            })
            .catch(function (error) {
                console.log(error);
                console.log('lỗi khi đăng nhập');
            });
        }
    },
    mounted(){
    this.userName = localStorage.getItem('name')
    if (this.userName || this.userName != '' || this.userName !=null){
      router.push({ name: 'home'})
    }
  },
    
}
</script>
<style lang="">
    
</style>