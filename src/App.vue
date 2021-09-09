<template>
  <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
  <div class="appContainer">
    <!-- class = "isCollapseOpen  ? 'w20' : 'w5'" -->
      <div  :class="isMobileExist  && isCollapseOpen ? 'w100' : (isMobileExist && !isCollapseOpen ? 'w10' : (!isMobileExist && isCollapseOpen ? 'w20' : 'w5'))">
      <Sidebar :path="path" :logout="logout"  :data="data" :isLoggedIn="isLoggedIn" :isCollapseOpen="isCollapseOpen"  @toggleCollapse="toggleCollapse"  />
      </div>  
      <!-- <div class="main" :class = "isCollapseOpen  ? 'w80' : 'w95' "> -->
        <div class="main" :class="isMobileExist  && isCollapseOpen ? 'dnone' : (isMobileExist && !isCollapseOpen ? 'w90' : (!isMobileExist && isCollapseOpen ? 'w80' : 'w95'))">
        my app
         </div>
    </div>
</template>

<script>
import Sidebar from './components/sidebar.vue'
import { isMobile } from 'mobile-device-detect';

export default {
  name: 'App',
    data(){
            return {
                data: [
  { img: "", name: "Dashboard", url: "/dashboard" },
  { img: "", name: "Document", url: "/document" },
  { img: "", name: "Service availibility", url: "/service" }],
  isLoggedIn: true,
  path: window?.location?.pathname,
  isMobileExist : isMobile,
  logout :
  { img: "", name: "LogOut", url: "/" },
    isCollapseOpen :isMobile ? false : true,
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

.dnone{
  display: none !important;
}

.appContainer {
  /* display : inline-flex; */
  display: flex;
   width : '100%'
}
.w20{
width : 20%;
}

.w90{
  width : 90%;
}

.w5{
    width : 5%;
}

.w100 {
  width : 100vw;
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