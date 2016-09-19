<template>
  <div class="navbar">
    <div class="menu">
      <ul class="nav-menu">
        <li v-for="menu in data"><a href="{{menu.url}}">{{menu.text}}</a>
          <!-- <ul class="subs" v-if="menu.childItem">
            <li  v-for="child in menu.childItem">
              <div class="subs-content">
                <div class="subs-title"><img src="http://temp.im/24x24">{{child.text}}</div>
                 <a v-for="sub in child.subItems" class="subs-text-a" style="border:none;float:left;width:auto;" href="http://www.baidu.com" target="_blank">{{sub.text}}</a>
              </div>
            </li>
          </ul> -->
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
  ul.left-menu li {
    height: 40px;
    line-height: 40px;
    border-bottom: 1px black solid;
  }
  .nav-menu {
    background-color: yellowgreen;
  }
  .nav-menu li a {
    -moz-transition:0.5s;
    -o-transition:0.5s;
    -webkit-transition:0.5s;
    border:1px solid #E8E8E8;
    color:#000000;
    display:block;
    font-size:16px;
    line-height:35px;
    padding:5px 20px;
    text-decoration:none;
    transition:0.5s;
  }

  .nav-menu li:hover > a {
    background:blue;
    border:1px solid #ffffff;
    color:#fff;
    border-radius: 4%;
    transform: rotateX(180deg);
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
    margin-left: 30px;
  }
  
  .menu-bottom-nav{
    width: 100%;
    background: red;
    height: 40px;
    margin: 0 auto;
    font-size: 16px;
    font-weight: bolder;
    line-height: 40px;
    margin-top: -9px;
  }
  @media(min-width: 1200px){
    .menu {
      position:relative;
      background:#ffffff;
      width:100%;
      
    }
    .nav-menu ul {
      height:0;
      left:161px;
      overflow:hidden;
      position:absolute;
      top:1px;
    }
  }
  @media screen and (min-width:990px) and (max-width: 1200px){
    .menu {
      position:relative;
      background:#ffffff;
      width:100%;
      
    }
    .nav-menu ul {
      height:0;
      left:9%;
      overflow:hidden;
      position:absolute;
      top:1px;
    }
    /*.nav-menu li:hover ul.subs {
      height:91%;
      width:70%;
      text-align: left;
    }
    .nav-menu ul li {
      -moz-transition:0.1s;
      -o-transition:0.1s;
      -webkit-transition:0.1s;
      opacity:0;
      transition:0.1s;
      width:100%;
    }*/
  }
</style>
