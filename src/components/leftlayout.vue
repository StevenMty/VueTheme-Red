<template>

<div class="container-fluid admin-panel">
  <div class="row">
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
<style type="text/css">
@media(min-width: 1200px){
    .admin-panel{
      background-color: pink;
      width: 1170px;
    }
    .leftmenu-borad{
      height: 800px;
    }
  }
 @media screen and (min-width:990px) and (max-width: 1199px){
  .admin-panel{
      background-color: pink;
      width: 96%;
    }
    /*.leftmenu-borad{
      height: 800px;
    }*/
 }

</style>