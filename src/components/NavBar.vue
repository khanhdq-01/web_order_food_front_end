<template>
  <header v-if="$route.name !== 'login'">
    <nav class="navbar navbar-expand-lg bg-body-tertiary">
      <div class="container-fluid">
        <a class="navbar-brand" href="#"></a>
        <button
          class="navbar-toggler"
          type="button"
          data-bs-toggle="collapse"
          data-bs-target="#navbarSupportedContent"
          aria-controls="navbarSupportedContent"
          aria-expanded="false"
          aria-label="Toggle navigation"
        >
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarSupportedContent">
          <ul class="navbar-nav me-auto mb-2 mb-lg-0">
            <li class="nav-item me-3">
              <RouterLink to="/">Home</RouterLink>
            </li>
            <li v-if="role ==4 || role ==1 " class="nav-item me-3">
              <RouterLink to="/order">Order</RouterLink>
            </li>
            <li v-if="role ==4" class="nav-item me-3">
              <RouterLink to="/product">Product</RouterLink>
            </li>
            <li class="nav-item">
              <a href="#" @click="logout">Logout</a>
            </li>
          </ul>
          <div class="d-flex">
            <span>Hi, {{ name }}</span>
          </div>
        </div>
      </div>
    </nav>
  </header>
</template>

<script>
import axios from 'axios';
import router from '@/router';

export default {
  props: ['name', 'role'],
  methods: {
    logout() {
      axios.get('http://127.0.0.1:8000/api/auth/logout', {
        headers: {
          Authorization: `Bearer ${localStorage.getItem('token')}`
        }
      })
      .then(() => {
        this.clearLocalStorage();
        router.push({ name: 'login' });
      })
      .catch(error => {
        console.error(error);
        if (error.response && error.response.status === 401) {
          console.log('Token hết hạn, chuyển hướng về trang đăng nhập');
          this.clearLocalStorage();
          router.push({ name: 'login' });
        } else {
          console.log('Lỗi khác khi đăng xuất');
        }
      });
    },
    clearLocalStorage() {
      localStorage.removeItem('email');
      localStorage.removeItem('name');
      localStorage.removeItem('role_id');
      localStorage.removeItem('token');
    }
  }
};
</script>

<style scoped>
.navbar-nav .nav-item a {
  text-decoration: none;
  color: #000;
  font-weight: bold;
}

.navbar-nav .nav-item a:hover {
  color: #007bff;
}
</style>
