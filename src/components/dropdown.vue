<!-- 滑动弹出菜单组件 
Taoxin  2016-05-19
-->

<template>
  <div class="dropdown" style="height:200px;position:relative;">
   <ul class="dropdown-nav">
        <li v-for="menu in data"><a >{{menu.text}}</a>
            <ul class="subs" v-if="menu.childItem">
            <li  v-for="child in menu.childItem">
                 <a href="http://www.baidu.com" target="_blank">{{child.text}}</a>
            </li>
          </ul>
        </li>
    </ul>
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

/* main menu styles */

.dropdown-nav,.dropdown-nav ul {
    list-style:none;
    margin:0;
    padding:0;
}

.dropdown-nav {
    display: flex;
    /*position:absolute;
    top:23px;*/
}

.dropdown-nav ul {
    height:0;
    left:0;
    overflow:hidden;

}

.dropdown-nav li {
    position:relative;
    border-bottom: 1px solid #fff;
}

.dropdown-nav li a {
    -moz-transition:0.5s;
    -o-transition:0.5s;
    -webkit-transition:0.5s;
    /*background-color:#7770B4;*/
    /*border:1px solid #6E67A6;*/
    color:white;
    display:block;
    /*font-size:16px;*/
    line-height:10px;
    padding:5px 20px;
    text-decoration:none;
    transition:0.5s;
    width: 100px;
    background-color: #7a67ee;
}

.dropdown-nav li:hover > a {
    /*background:#8CCA33;*/
    border-color:#6E67A6;
    /*color:red;*/
}

.dropdown-nav li:hover ul.subs {
    height:auto;
    /*width:180px;*/
}

.dropdown-nav ul li {
    -moz-transition:0.5s;
    -o-transition:0.5s;
    -webkit-transition:0.5s;
    opacity:0;
    transition:0.5s;
    width:100%;
}

.dropdown-nav li ul li {
    -moz-transition-delay:0s;
    -o-transition-delay:0s;
    -webkit-transition-delay:0s;
    transition-delay:0s;
}

.dropdown-nav li:hover ul li {
    opacity:1;
    /*-moz-transition-delay:0.5s;
    -o-transition-delay:0.5s;
    -webkit-transition-delay:0.5s;
    transition-delay:0.5s;*/
}

.dropdown-nav ul li a {
    /*background:#7770B4;*/
    /*border-color:#6E67A6;*/
    /*color:#fff;*/
    line-height:1px;
    /*-moz-transition:1.5s;
    -o-transition:1.5s;
    -webkit-transition:1.5s;
    transition:1.5s;*/
}
ul.subs li a{
  background-image: none;
  /*border: 1px solid red;*/
} 
ul.subs li a:hover{
  background-image: none;
  /*border: 1px solid red;*/
} 

.dropdown-nav li:hover ul li a {
    line-height:10px;
}

.dropdown-nav ul li a:hover {
    /*background:#8CCA33;*/
    background-image: -webkit-gradient(linear, 0% 0%, 0% 95%, from(rgba(255, 255, 255, 0.5)), to(rgba(255, 255, 255, 0)));
    background-image: -moz-linear-gradient(-90deg, rgba(255, 255, 255, 0.5), rgba(255, 255, 255, 0));
    background-image: -o-linear-gradient(-90deg,rgba(255,255,255,0.5),rgba(255,255,25,0));
}
</style>
