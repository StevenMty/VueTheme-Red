<!--模态框-->
<template>
    <div class="modal-mask" v-show="show" transition="modal" @click="closemodal">
       <div class="modal-wrapper">
        <div class="modal-container">

            <div class="modal-header">
                <a class="close" @click="show = false"><span>&times;</span></a>
                <slot name="header">
                </slot>
            </div>

            <div class="modal-body">
                <slot name="body">
                    default body
                </slot>
            </div>

            <div class="modal-footer">
                <slot name="footer">
                </slot>
            </div>
        </div>
    </div>
</div>

</div>
</template>

<script>
    module.exports = {
        props: {
            show: {
                type: Boolean,
                required: true,
                twoWay: true
            },
            shadow:{
                type:Boolean,
                required:false,
                twoWay:false
            }
        },
        methods: {

            // 点击阴影处关闭modal
            closemodal(e){
                const classname = e.target.className;
                debugger;
                if(e.target.parentNode.className === 'close'){
                    this.show = false;
                }
                if (this.shadow){
                    if (classname === 'modal-wrapper'){
                        this.show = false;
                    } else if(e.target.parentNode.className === 'close'){
                        this.show = false;
                    } else{
                        this.show = true;
                    }
                } else{
                    if(e.target.parentNode.className === 'close'){
                        this.show = false;
                    }else{

                        this.show = true;
                    }
                }
                
            }
        }

    };
</script>
<style>
    .modal-mask {
        position: fixed;
        z-index: 9998;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background-color: rgba(0, 0, 0, .5);
        display: table;
        transition: opacity .3s ease;
    }

    .modal-wrapper {
        display: table-cell;
        vertical-align: middle;
    }

    .modal-container {
        max-width: 600px;
        min-width: 500px;
        margin: 0px auto;
        /*padding: 20px 30px;*/
        background-color: #fff;
        border-radius: 0px;
        box-shadow: 0 2px 8px rgba(0, 0, 0, .33);
        transition: all .3s ease;
        font-family: Helvetica, Arial, sans-serif;
        /*border:5px solid #999999;*/
        height: 300px;
        position: relative;
        z-index: 99999;
        border-radius: 3%;
    }
    .modal-header {
        min-height: 16.43px;
        padding: 0px; 
        border-bottom: 1px solid #e5e5e5;
        background: #F5F5F5;
        text-align: left;
        background-color: #B9D3EE;
    }
    .modal-header p {
        /*margin-top: 0;*/
        padding: 8px 0px 0 10px;
        color: black;
        font-weight: bolder;
    }

    .modal-body {
        margin: 0;
    }

    .modal-default-button {
        float: right;
    }

    /*
     * the following styles are auto-applied to elements with
     * v-transition="modal" when their visiblity is toggled
     * by Vue.js.
     *
     * You can easily play with the modal transition by editing
     * these styles.
     */

     .modal-enter, .modal-leave {
        opacity: 0;
    }

    .modal-enter .modal-container,
    .modal-leave .modal-container {
        -webkit-transform: scale(1.1);
        transform: scale(1.1);
    }
    a.btn.btn-cancel{
        color: #333;
        background-color: #dedede;
        border: 1px solid #e3e3e3;
        border-bottom: 1px solid #aaa;
        background-size: 100%;
        border-radius: 0px;
    }
    a.btn.btn-submit{
        color: #ffffff;
        background-color: #2db3a6;
        border: 1px solid #e3e3e3;
        border-bottom: 1px solid #aaa;
        background-size: 100%;
        border-radius: 0px;
    }
    .modal-header .close {
        margin: 6px 15px;
        -webkit-transition: -webkit-transform 0.2s ease-out;
        -moz-transition: -moz-transform 0.2s ease-out;
        -o-transition: -o-transform 0.2s ease-out;
        -ms-transition: -ms-transform 0.2s ease-out;
    }
    .modal-header .close:hover{
        -webkit-transform: rotateZ(180deg);
        -moz-transform: rotateZ(180deg);
        -o-transform: rotateZ(180deg);
        -ms-transform: rotateZ(180deg);
        transform: rotateZ(180deg);
    }
    .modal-footer {
        padding: 0 0 15px 0;
        text-align: justify;
        border-top: none; 
    }
    button{
        border: none;
        background-color:  #FF8C00;
        border-radius: 2px;
    }
    button:hover{
        background-color: #DAA520;
        transition: 1s;
        color: white;
        border-radius: 2px;
    }
</style>