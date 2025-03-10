<template lang="">
  <!-- navbar -->
   <NavBar :name=userName :role="roleId"/>
  <div class = "home">
   <span style="text-align:center" > {{userName}} </span>
  </div>
</template>
<script>
import NavBar from '@/components/NavBar.vue';
import router from '@/router';
export default {

  components:{
    NavBar
  },
  data() {
    return {
      userName: '',
      roleid:''
    }
  },
  mounted(){
    this.userName = localStorage.getItem('name')
    this.roleId = localStorage.getItem('role_id')
    if (!this.userName || this.userName == '' || this.userName ==null){
      router.push({ name: 'login'})
    }
  },
}
</script>
<style lang="">
  
</style>