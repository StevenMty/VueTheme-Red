<!-- 搜索组件
Taoxin   2016-05-19
 -->

 <template>
     <div class="search-bar">
       <ul class="search-menu">
          <li >
          <a>{{queryOne}}</a>
            <ul class="childs">
              <li><a @click="choose">{{queryTwo}}</a></li>
            </ul>
          </li>
        </ul>
        <input class="form-control input-search-bar" :placeholder="placeholder" v-model="value"/>
        <button class="btn-search-bar" @click="search">搜索</button>
      </div>
 </template>
<script>
  module.exports = {
    props: {
      value: {
        type: String,
        required: false,
        twoWay: true
      },
      placeholder: {
        type: String,
        required: false,
        twoWay: false
      }
    },
    data() {
      return {
        isactive: false,
        queryOne:'商品',
        queryTwo:'商家',
        queryKey:1,
      };
    },
    compiled(){
    },
    methods: {
      search(){
         this.$parent.search();
      },
      choose(){
        this.queryKey = this.queryKey * -1;
        if (this.queryKey === 1) {
          this.queryOne = '商品';
          this.queryTwo = '商家';
          this.placeholder='请输入商品名称、地址等';
        } else{
          this.queryOne = '商家';
          this.queryTwo = '商品';
          this.placeholder='请输入商家名称、地址等';
        }
      }
    }
  };
</script>

 <style type="text/css">
 .search-bar{
    width: 598px;display: flex;
    border:1px solid #ccc;
 }
 .dropdown-search-bar{
    width: 400px;
 }
 .btn-search-bar{
    width: 100px;
    height: 35px;
    padding: 0 !important;
    margin: 0 !important;
 }
.input-search-bar{
    width: 416px;
    height: 35px;
    border-radius: 0px;
    padding: 0 !important;
    margin: 0 !important;
}
.input-search-bar:focus{
    border-radius: 0px;
    border:none;
}
/*.nav>li>a:focus, .nav>li>a:hover {
    text-decoration: none;
    outline: none;
    background-color: #eee;
}
.nav>li>a {
    position: relative;
    display: block;
    padding: 4px 15px;
}
.nav-tabs>li {
    float: left;
    margin-bottom: 0px;
    height: 28px;
}*/
/*.serach-a{
  float: left;
  width: 70px;
  height: 35px;
  border:1px solid;
  padding: 4px;
  font-size: 18px;
}*/

.search-menu,.search-menu ul {
    list-style:none;
    margin:0;
    padding:0;
}

.search-menu {
    position:relative;
}

.search-menu ul {
    height:0;
    left:0;
    overflow:hidden;
    position:absolute;
    top:35px;
}

.search-menu li {
    float:left;
    position:relative;
}

.search-menu li a {
    /*border:1px solid #f3f3f3;*/
    color:black;
    display:block;
    font-size:18px;
    line-height:10px;
    padding:10px;
    text-decoration:none;
    width: 80px;
    height: 35px;
    background-image: url('../../../static/img/arrow.png');
    background-repeat:no-repeat;
    background-position: 60px 10px;
}

.search-menu li:hover > a {
    /*background:#8CCA33;*/
    color:red;
    /*border-bottom:1px solid red;*/
    background-image: url('../../../static/img/arrow_1.png');
    background-repeat:no-repeat;
}
ul.childs li a{
  background-image: none;
} 
ul.childs li a:hover{
  background-image: none;
  /*border: 1px solid red;*/
} 

.search-menu li:hover ul.childs {
    height:auto;
}

.search-menu ul li {
    opacity:0;
    width:100%;
}
.search-menu li:hover ul li {
    opacity:1;
}

.search-menu ul li a {
    line-height:1px;
}

.search-menu li:hover ul li a {
    line-height:10px;
}

.search-menu ul li a:hover {
    background-color: #ccc;
}

 </style>

