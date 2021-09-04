<template>
  
    <div class = "mainWrapper">
    <div class="menuItemWrapper">
       <div class="menuTitleWrapper">
          <label class="title" v-bind:class="getClass()">
            CIMB
          </label>
          <div
            @click="toggleCollapse"
          >
            <div class="menuIcon"></div>
            <div class="menuIcon"></div>
            <div class="menuIcon"></div>
          </div>
        </div>
        <div class="separater"></div>
    </div>



     <ul class="menuList">
        <li class="pl-2" v-for="(item, index) in data" v-bind:key="index" >
             <a :href ="item.url">
                    <img class="list-img" src="@/assets/logo.png" alt="logo" />
                             <label class="label" v-bind:class="getClass()">
                      {{item.name}}
                    </label>
                  </a>
        </li>
        </ul>


        <div class="logout pl-2">
          <a href = "/">
            <span>
              <img class="list-img" src="@/assets/logo.png" alt="logo" />
                        <label class="label" v-bind:class="getClass()">

                Logout
              </label>
            </span>
          </a>
        </div>
    </div>

 </template>

<script>
import { isMobile } from 'mobile-device-detect';

export default {
  name: "Sidebar",
  props: {
    msg: String,
    data: Array,
    isLoggedIn: Boolean,
    isCollapseOpen: Boolean,
  },
   data() {
    return {
      isCollapseOpenLocal: this.isCollapseOpen,
      isMobileDetected : isMobile,
    };
  },
  methods: {


 getClass(){
    return {
     'dNoneFix': !this.isCollapseOpenLocal,
      '': this.isCollapseOpenLocal
    }
  },

    toggleCollapse: function(){
      console.log("this.isCollapseOpenLocal",this.isCollapseOpenLocal);
      this.isCollapseOpenLocal = !this.isCollapseOpenLocal;
      this.$emit('toggleCollapse' , this.isCollapseOpenLocal)
    }
  } ,
   /* data(){
            return {
              isCollapseOpen : true,
            }},
            */
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
 

 .mainWrapper{
    height: 100vh;
    background-color: #333;
    width : 100%;
}
.menuItemWrapper{
    background: #333;
    padding: 2em;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
}

.menuList{
    list-style-type: none;
    padding: 0;
    


  
}
.menuList a {
        display: flex;
        margin-bottom: 1em;
        line-height: 2;
        cursor: pointer;
        text-decoration: none;
    }

  .list-img {
        width: 2em;
        height: 2em;
            margin-top: auto;
    margin-bottom: auto;
        margin-right: 1em;
    }

.label {
    font-size: 1.5em;
    color: #fff;
    cursor: pointer;

}

.menuTitleWrapper{
    display: flex;
    justify-content: space-between

}

.menuIcon {
    width: 2.53em;
    height: 0.4em;
    background-color: #fff;
    margin: 0.3em 0;
    border-radius: 0.3em;
    cursor: pointer;
  }

.title {
    color: #fff;
    font-size: 2em;
    font-weight: 700;
}

.separater{
    border-bottom: 2px solid #ddd;
    margin-left: -2em;
    margin-right: -2em;
    margin-top: 1em;
}

.logout{
    position: absolute;
    bottom: 1em;
    cursor: pointer;
    
}

.dNone{
    display: none;
}

.dNoneFix{
  padding-left:25%;
  display: none;
}

.fixWidth{
    width: 100px !important;
}


.fullWidth{
    width: 100vw;
}


.logout a {
        text-decoration: none;
    }
   .logout  span {
        display: flex;
        line-height: 2; 
        text-decoration: none;
    }
   

.pl-2 {
  padding-left: 2em;
}


</style>