<template lang="">
  <div class = "home">
   {{userName}}
  </div>
</template>
<script>
import router from '@/router';
export default {
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