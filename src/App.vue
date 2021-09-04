<template>
  <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
  <div class="appContainer">
      <div  :class = "isCollapseOpen  ? 'w20' : 'w5' ">
      <Sidebar  :data="data" :isLoggedIn="isLoggedIn" :isCollapseOpen="isCollapseOpen"  @toggleCollapse="toggleCollapse"  />
      </div>  
      <div class="main" :class = "isCollapseOpen  ? 'w80' : 'w95' ">
        my app
         </div>
    </div>
</template>

<script>
import Sidebar from './components/sidebar.vue'

export default {
  name: 'App',
    data(){
            return {
                data: [
  { img: "", name: "Dashboard", url: "/dashboard" },
  { img: "", name: "Document", url: "/document" },
  { img: "", name: "Service availibility", url: "service" }],
  isLoggedIn: true,
    isCollapseOpen : true,
            };
        },
  components: {
    Sidebar
  },
  methods: {
    toggleCollapse: function (event) {
      // debugger;
      console.log(event)
        this.isCollapseOpen = event;
    }
  }

}
</script>

<style>
#app {
  margin: 0 !important;
}

.appContainer {
  /* display : inline-flex; */
  display: flex;
   width : '100%'
}
.w20{
width : 20%;
}

.w5{
    width : 5%;
}


.w80{
    width : 80%;
    }
    
    .w95{
        width : 97%;
    }
    .main {
       background : red ;
        box-sizing :border-box;
        display : flex ;
        justify-content : center;
        align-items : center
    }
</style>
