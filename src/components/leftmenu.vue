<template>
  <div class="navbar">
      <div class="">
          <div class="img-g" style="background-color:white;"><a href="https://www.xgou168.com/"><img src="./../../static/img/logo.png"></a></div>
           <ul class="left-menu" >
             <li v-for="menu in data">
                <a v-if="!menu.child" @click="goto(menu.url)">{{menu.text}}</a>
                <div v-else @click="showSubMenu(menu.id)">{{menu.text}}</div>
                <ul v-if="menu.child" v-show="activeindex==menu.id">
                  <li v-for="submenu in menu.child"><a @click="goto(submenu.url)">{{submenu.text}}</a></li>
                </ul>
             </li>
           </ul>
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
   props: ['data', 'activeindex'],
   methods: {
     showMenu() {
       this.isShow = !this.isShow;
     },
     showSubMenu(id) {
       if (this.activeindex === id) {
         this.activeindex = 0;
       } else {
         this.activeindex = id;
       }
     },
     goto(urlObject) {
       if (typeof(urlObject) === 'string') {
         window.router.go({
           path: urlObject
         });
       } else {
         window.router.go(urlObject);
       }
     }
   }
 };
 </script>
<style type="text/css">
*{
  margin: 0;
  padding: 0;
}
.navbar{
    width: 173px !important;
  }
ul.left-menu{
  list-style: none;
}
ul.left-menu li{
    min-height: 40px;
    line-height: 40px;
    border: none !important;
    background-color: #fff;
}
ul.left-menu li:hover{
  background-color: #eeeed1;

}
ul.left-menu li a{
  text-decoration: none;
  color: #000;
  font-size: 1em;
  cursor: pointer;
}

</style>