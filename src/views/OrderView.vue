<template lang="">
    <div>
        <NavBar :name=userName />
        <div class="container-fluid mt-5">
          <div class="row">
            <!-- item list -->
            <div class="col-12 col-sm-8 mb-3">
              <div class="col-12">
                <input type="text" class="form-control" placeholder="Search Here" />
              </div>

              <hr />
              <!--item list box-->
                <div class="col-12 ">
                  <div class="row">
                    <div class="col-12 col-sm-6 col-md-4 col-lg-3 mb-3">
                      <div class="card">
                        <img class="card-img-top" src="..." alt="Card image cap">
                        <div class="card-body text-center">
                          <h5 class="card-title">Card title</h5>
                          <p class="card-text">Rp 15000</p>
                        </div>
                      </div>
                    </div>
                    <div class="col-12 col-sm-6 col-md-4 col-lg-3 mb-3">
                      <div class="card">
                        <img class="card-img-top" src="..." alt="Card image cap">
                        <div class="card-body text-center">
                          <h5 class="card-title">Card title</h5>
                          <p class="card-text">Rp 15000</p>
                        </div>
                      </div>
                    </div>
                    <div class="col-12 col-sm-6 col-md-4 col-lg-3 mb-3">
                      <div class="card">
                        <img class="card-img-top" src="..." alt="Card image cap">
                        <div class="card-body text-center">
                          <h5 class="card-title">Card title</h5>
                          <p class="card-text">Rp 15000</p>
                        </div>
                      </div>
                    </div>
                    <div class="col-12 col-sm-6 col-md-4 col-lg-3 mb-3">
                      <div class="card">
                        <img class="card-img-top" src="..." alt="Card image cap">
                        <div class="card-body text-center">
                          <h5 class="card-title">Card title</h5>
                          <p class="card-text">Rp 15000</p>
                        </div>
                      </div>
                    </div>
                </div>
              </div>
            </div>
            <!-- item list -->
            <div class="col-12 col-sm-4 mb-3 bordered" >
              Card title
            </div>
          </div>
        </div>
    </div>
</template>
<script>
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
    this.getItem()
  },
  methods:{
    getItems() {
      
    }
  }
}
</script>
<style>
  .bordered {
    border: solid 1px;
  }
    
</style>