<template lang="">
  <!-- navbar -->
   <NavBar :name=userName />
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
      userName: ''
    }
  },
  mounted(){
    this.userName = localStorage.getItem('name')
    if (!this.userName || this.userName == '' || this.userName ==null){
      router.push({ name: 'login'})
    }
  },
}
</script>
<style lang="">
  
</style>