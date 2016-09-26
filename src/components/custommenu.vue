<template>
  <div class="navbar">
    <div class="menu" style="display: block">
      <ul class="nav-menu">
        <li v-for="menu in data"><a href="{{menu.url}}">{{menu.text}}</a>
          <ul class="subs" v-if="menu.childItem" style="position: fixed;top: 160px;left: 180px; ">
            <li  v-for="child in menu.childItem" class="first-li">
              <div class="subs-content">
                <div class="subs-title"><img src="http://temp.im/24x24">{{child.text}}</div>
                 <a v-for="sub in child.subItems" class="subs-text-a" style="border:none;float:left;padding-left:40px;width:auto;" href="http://www.baidu.com" target="_blank">{{sub.text}}</a>
              </div>
            </li>
          </ul>
        </li>

      </ul>
      <div class="menu-bottom-nav">
        <!-- <img src="http://temp.im/154x64"> -->
        <a href="{{bottomnav.url}}" style="color:#ffffff;">{{bottomnav.text}}</a>
    </div>
    </div>
    
    <div class="navbar-header">
      <button class="navbar-toggle" type="button" @click="showMenu">
        <span class="icon-bar" :class="{xbar:isShow}"></span>
        <span class="icon-bar" :class="{xbar:isShow}"></span>
        <span class="icon-bar" :class="{xbar:isShow}"></span>
      </button>
    </div>
  </div>
</template>
<script>
  module.exports = {
    props: [
        'data',
        'bottomnav'
    ],
    methods: {
      showMenu() {
        this.isShow = !this.isShow;
      },
      test() {
      }
    }
  };
</script>
<style type="text/css">
  *{
    margin: 0;
    padding: 0;
  }
  ul{
    list-style: none;
  }
  .nav-menu {
    background-color: yellowgreen;

  }
  .nav-menu li a {
    height: 40px;
    width: 100%;
    color: black;
    display: inline-block;
    border-top:1px solid #fff;
    line-height: 40px;
  }
  .nav-menu li:hover > a {
    background:blue;
    border:1px solid #ffffff;
    color:#fff;
    border-radius: 4%;
    /*transform: rotateX(180deg);*/
  }

  .nav-menu li:hover ul.subs {
    height:91%;
    width:600px;
    text-align: left;
  }

  .nav-menu ul li {
    -moz-transition:0.1s;
    -o-transition:0.1s;
    -webkit-transition:0.1s;
    opacity:0;
    transition:0.1s;
    width:100%;
  }
  .nav-menu li:hover ul li {
    opacity:1;
    -moz-transition-delay:0.1s;
    -o-transition-delay:0.1s;
    -webkit-transition-delay:0.1s;
    transition-delay:0.1s;
  }
  .subs-content{
    height: 80px;
  }
  .subs-title{
    border-bottom: 1px solid;
    width: 100%;
    margin-left: 3o0px;
  }
  
  .menu-bottom-nav{
    width: 100%;
    background: red;
    height: 40px;
    font-size: 16px;
    font-weight: bolder;
    line-height: 40px;
    margin-top: 1px;
  }
</style>
