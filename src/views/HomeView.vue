<template lang="">
  <!-- navbar -->
   <NavBar :name=userName :role= "roleId"/>
  <div class = "home">
   <span style="text-align:center" > {{userName}} </span>
  </div>
</template>
<script>
import router from '@/router';
import NavBar from '@/components/NavBar.vue';
export default {

  components:{
    NavBar
  },
  data() {
    return {
      userName: '',
      role:''
    }
  },
  mounted(){
    this.userName = localStorage.getItem('name')
    this.roleId = localStorage.getItem('role_id')
    // if (this.roleId != 4 && this.roleId !=1){
    //   router.push({ name: 'home'})
    // }
    if (!this.userName || this.userName == '' || this.userName ==null){
      router.push({ name: 'login'})
    }
  },
}
</script>
<style lang="">
  
</style>