<template>
    <div class="p-button">
        <upload :uploadurl.sync='url'></upload>
        <a>{{url}}</a>
    </div>
</template>
<script>
  import upload from './../components/qiniu_upload.vue';
  export default {
    components: {
      upload,
    },
    data(){
    return {
      url:''
    };
  },
    watch: {
    },
    compiled(){
    }
  };
</script>
<style type="text/css">
  .p-button{
    width: 100px;
    height: 40px;
    border-radius: 5px;
    background-color: greenyellow;
    line-height: 40px;
  }
  a{
    text-decoration: none !important;
    cursor: pointer;
  }
</style>