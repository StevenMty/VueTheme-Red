<template>
<div class="fixedeasein" :class="{'navbar-fixed-top':navIsShow}">
<!-- <div class="navbar " v-el:navmenu> -->
      <div class="container navborder-red" :style="{ background: bgColor}">
        <div class="navbar-header">
          <button class="navbar-toggle" type="button" @click="showMenu">
            <span class="icon-bar" :class="{xbar:isShow}"></span>
            <span class="icon-bar" :class="{xbar:isShow}"></span>
            <span class="icon-bar" :class="{xbar:isShow}"></span>
          </button>
          <a class="navbar-brand hidden-sm" href="">VueTheme-Red</a>
        </div>
        <div class="navbar-collapse" style="height: 1px;" :class="{showbyopacity:isShow,navbaran:isShow}">
          <ul class="nav navbar-nav navbar-right" :class="{showtranslate:isShow}">
            <li v-for="menu in data"><a href="/#{{menu.url}}">{{menu.text}}</a></li>
            <li class="hidden-sm"><a href="#">About</a></li>
            <li class="bgc-navbar">
              NAVBAR-BGC
              <ul class="navbar-f">
                <li><p class="bgc-One" style="background-color:#EE9A00;" @click="changeColor('#EE9A00')"></p></li>
                <li><p class="bgc-Two" style="background-color:#8DB6CD;" @click="changeColor('#8DB6CD')"></p></li>
                <li><p class="bgc-three" style="background-color:#7D26CD;" @click="changeColor('#7D26CD')"></p></li>
                <li><p class="bgc-four" style="background-color:#008B45;" @click="changeColor('#008B45')"></p></li>
                <li><p class="bgc-five" style="background-color:#8B8386;" @click="changeColor('#8B8386')"></p></li>
              </ul>
            </li>
          </ul>
        </div>
      </div>
    </div>
</template>
<script>
 module.exports = {
   props:['data'],
   data() {
     return {
       isShow: false,
       navIsShow: false,
       bgColor:'#2196F3',
       show:false
     };
   },
   methods: {
     showMenu() {
       this.isShow = !this.isShow;
     },
     scrollFixed() {
       let timer;
       window.onscroll = () => {
         if (timer) {
           clearTimeout(timer);
         }
         if (this.navIsShow){
           this.navIsShow=false;
         }
         timer = setTimeout(() => {
           this.navIsShow = true;
         }, 500);
       };
     },
     changeColor(color){
      this.bgColor = color;
     },
     test(){
      alert(111)
     }
   }
 };
</script>
<style type="text/css">
@keyframes down {
  0%{top: 0px}
  25%{top: 20px}
  40%{top: 40px}
  60%{top: 60px}
  80%{top: 80px}
  100%{top: 100px}
}
.navbar-f{
  /*background-color: red;*/
  position: fixed;
  width: 103px;
  top: 100px;
  display: none;
  z-index: 2;
  box-shadow: 2px 2px  5px #ccc;
  text-align: center;
  animation: down .5s ease-out 1;
}
.navbar-f>li{
  width: 100%;
  height: 35px;
  border:none;
  position: relative;
  border-top: 1px solid #ccc;
   transition: 2s;
  -moz-transition: 2s; /* Firefox 4 */
  -webkit-transition: 2s; /* Safari 和 Chrome */
  -o-transition: 2s; /* Opera */
}
.navbar-f>li>p{
  width: 15px;
  height: 15px;
  border-radius: 50%;
  position: absolute;
  left: 44px;
  top: 10px;
}
.bgc-navbar:hover>.navbar-f{
  display: block;
}
* ul{
  margin: 0;
  padding: 0;
}
body{
  margin: 0 auto;
}
.navbar-fixed-top .navbar-toggle{
  z-index: 1;
}
.fixedeasein{
  -webkit-transition: all .5s ease;
  -moz-transition: all .5s ease;
  transition: all .5s ease;
}
.menu-animate{
  -webkit-transition: visibility .5s ease;
  -moz-transition: visibility .5s ease;
  transition: visibility .5s ease;
  visibility: visible;
}
.navbar-header{
  width: 260px !important;
}
.navbar-brand{
  font-size: 2em;
  padding-top: 15%;
  color: #ffffff;
  font-weight: bold;
}
.navbar-right{
  display: flex;
}
.navborder-red {
  width: 100%;
  min-height: 100px;
  max-height: 100px;
  position: fixed;
  top: 0;
  z-index: 9999;
}
.navborder-red .icon-bar {
  background-color: #888;
  top:0;
}
.navbar-nav>li>a{
    font-weight: bold;
    font-size: 1em;
    text-transform: uppercase;
    letter-spacing: 1px;
    color: #ffffff;
    -webkit-transition: all .5s ease;
    -moz-transition: all .5s ease;
    transition: all .5s ease;
    padding-bottom: 40px;
    padding-top: 30px;
    display: inline-block;
    line-height: 30px;
    cursor: pointer;
    width: 100%;
}
.bgc-navbar{
  font-weight: bold;
    font-size: 1em;
    text-transform: uppercase;
    letter-spacing: 1px;
    color: #ffffff;
    -webkit-transition: all .5s ease;
    -moz-transition: all .5s ease;
    transition: all .5s ease;
    padding-bottom: 40px;
    padding-top: 30px;
    display: inline-block;
    line-height: 30px;
    cursor: pointer;
}
.navbar-nav>li>a:hover{
  text-decoration: none;
  background-color: #3F51B5 ;
}
.bgc-navbar:hover{
  text-decoration: none;
  background-color: #3F51B5 ;
}
.navbaranimal{
    transform:translateY(100px);
    transition: -webkit-transform 400ms cubic-bezier(0.215, 0.61, 0.355, 1) 0ms;
    background-color: rgb(255, 255, 255);
  }
.showbyopacity{
  opacity:1!important;
}
.showtranslate{
  transform: translate3d(0px, 0px, 0px)!important;
}
.bgc-title{

}
@media (max-width: 780px) {
  .navbar-brand{
    font-size: 2em;
    padding-top: 5%;
    color: #ffffff;
    font-weight: bold;
  }
  .navbar-nav>li>a{
    padding-bottom: 15px;
    padding-top: 15px;
  }
  .navbar-collapse {
    opacity:0;
  }  
  .navbaran{
    transition: opacity 800ms cubic-bezier(0.39, 0.575, 0.565, 1) 300ms;
  }
  .navbar-collapse .navbar-right{
    transform: translate3d(0px, -40px, 0px);
    transition: -webkit-transform 500ms cubic-bezier(0, 1, 1, 0.73) 300ms;
  }
}
.navbar-header .navbar-toggle {
  width: 40px;
  height: 40px;
}
.navbar-header .navbar-toggle .xbar{
   position: absolute;
   right: 10px;
    -webkit-transform-origin: 50% 50%;
    -moz-transform-origin: 50% 50%;
    -ms-transform-origin: 50% 50%;
    -o-transform-origin: 50% 50%;
    transform-origin: 50% 50%;
    opacity: 1;
    -webkit-transition-delay: 0ms;
    -moz-transition-delay: 0ms;
    -o-transition-delay: 0ms;
    transition-delay: 0ms;
    -webkit-transition: top, -webkit-transform 200ms cubic-bezier(0, 1, 1, 0.73) 100ms;
    -moz-transition: top, -moz-transform 200ms cubic-bezier(0, 1, 1, 0.73) 100ms;
    -o-transition: top, -o-transform 200ms cubic-bezier(0, 1, 1, 0.73) 100ms;
    transition: top, transform 200ms cubic-bezier(0, 1, 1, 0.73) 100ms;
}
.navbar-header .navbar-toggle .xbar:nth-child(1) {
    top: 16px;
    -webkit-transform: rotate(45deg) scaleX(1.442);
    -moz-transform: rotate(45deg) scaleX(1.442);
    -o-transform: rotate(45deg) scaleX(1.442);
    transform: rotate(45deg) scaleX(1.442);
}
.navbar-header .navbar-toggle .xbar:nth-child(2) {
    opacity: 0;
}
.navbar-header .navbar-toggle .xbar:nth-child(3) {
    top: 13px;
    -webkit-transform: rotate(-45deg) scaleX(1.442);
    -moz-transform: rotate(-45deg) scaleX(1.442);
    -o-transform: rotate(-45deg) scaleX(1.442);
    transform: rotate(-45deg) scaleX(1.442);
}
</style>