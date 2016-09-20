<template>

<div class="container-fluid admin-panel">
  <div class="row">
    <!-- <div class="button-hide" @click="showMenu">hide</div> -->
    <div class="col-md-2 leftmenu-borad">
      <slot name="left_menu"></slot>
    </div>
    <div class="col-md-10">
      <div class="main-container" >
        <slot name="left_container"></slot>
      </div>
    </div>
  </div>
</div>
</template>
<script>
 module.exports = {
  data(){
    return {
      isShow:false
    }
  },
   methods: {
     showMenu() {
       this.isShow = !this.isShow;
       console.info(this.isShow)
     },
   }
 };
 </script>
<style type="text/css">
  *{
    margin: 0;
    padding: 0;
  }
  .admin-panel{
    width: 90% !important;
    background-color: #F7F7F7;
    margin: 0 auto;
   /* padding: 0;*/
  }
  .row{
    width: 100%;
    display: flex;
  }
  .leftmenu-borad{
    width: 175px !important;
    margin: 0;
    padding: 0;
  }
  .button-hide{
    width: 50px;
    height: 50px;
    border-radius: 25px;
    background-color: #00bcd4;
    line-height: 50px;
    color: #fff;
    font-size: 1.5em;
    position: absolute;
    cursor: pointer;
    top: 50%;visibility: hidden;
  }
  /*@keyframes move{
    0%{position: absolute;left: 0;}
    20%{position: absolute;left: -35px;}
    40%{position: absolute;left: -70px;}
    60%{position: absolute;left: -105px;}
    80%{position: absolute;left: -140px;}
    100%{position: absolute;left: -175px;}
  }*/
  @media screen and (max-width: 780px){
  .leftmenu-borad{
    /*animation:move 0.5s infinite;
    -webkit-animation:move 0.5s infinite;*/
    visibility: hidden;
  }
   .button-hide{
    visibility: visible;
   }
}
</style>