<template>
  <div>
    <!--input-->
    <div class="col-md-12 col-lg-12">
      <h2>Input</h2>
      <mdinput :value.sync="firstName" class="move-P">
        <label slot="input-lable">FirstName</label>
      </mdinput>
      <mdinput :value.sync="lastName" class="move-P">
        <label slot="input-lable">LastName</label>
      </mdinput>
      <div class="two-Input">
        <span class="span-O">
        <input type="text" class="input-O" @blur="checkSearch" v-model="seach">
        <label class="input-L" @click='narrow' :style="{ width:swidth,background:bgColor }">
          <span class="span-T">firstName</span>
        </label>
      </span>
      <span class="span-O span-A">
        <input type="text" class="input-O" @blur="checkSearchA" v-model="seachA">
        <label class="input-A" @click='narrowA' :style="{ width:swidthA,background:bgColorA }">
          <span class="span-A">lastName</span>
        </label>
      </span>
      </div>
      <span class="name-f">firstName:<span style="color:red">{{firstName}}</span></span>
      <span class="name-f">lastName:<span style="color:red">{{lastName}}</span></span>
    </div>
    <!--radio-->
    <div class="col-md-12 col-lg-12">
      <h2>Radio</h2>
      <span class="select-c">Select your like color:['{{radio}}']</span>
      <mdradio :value.sync="radio" radio-value="green" :name.sync="radio"><label slot="radio-text" >Green</label>
      </mdradio>
      <mdradio :value.sync="radio" radio-value="yellow" :name.sync="radio"><label slot="radio-text">Yellow</label>
      </mdradio>
    </div>
    <!--checkbox-->
    <div class="col-md-12 col-lg-12">
      <h2>CheckBox</h2>
      <div style="text-align: left">
        <p>Your hobbies: {<p>"basketball":{{checkbox.basketball}}</p><p>"football":{{checkbox.football}}</p>}</p>
      </div>
      <mdcheckbox :value.sync="checkbox.basketball" checkbox-value="green" :name.sync="checkbox1"><label
        slot="checkbox-text">Basketball</label></mdcheckbox>
        <mdcheckbox :value.sync="checkbox.football" checkbox-value="yellow" :name.sync="checkbox2"><label
          slot="checkbox-text">Football</label></mdcheckbox>
        </div>
        <!-- Select -->
        <div class="col-md-12 col-lg-12">
          <h2>Select</h2>
          <mdselect :value.sync="selected" :options="options" :multiple=false :placeholder="choose"></mdselect>
        </div>


        <!-- Textarea -->
        <div class="col-md-12 col-lg-12">
          <h2>Textarea</h2>
          <mdtextarea :value.sync="textarea">
            <label slot="input-lable">Textarea</label>
          </mdtextarea>
        </div>
        <!-- Counter -->
        <div class="col-md-12 col-lg-12">
          <h2>Counter</h2>
          <mdcounter :counter.sync="counter" ></mdcounter>
          <mdcounter :counter.sync="counter" :type.sync="vertial">
          </mdcounter>
          <span>current Number:{{counter}}</span>
        </div>


        <div class="col-md-12 col-lg-12" style="height:100px">
          <mdsearch :value.sync="searchvalue"></mdsearch>
        </div>
        <div class="col-md-12 col-lg-12">
         <mdverifycode :verify.sync="result"></mdverifycode>
       </div>
       <div class="col-md-12 col-lg-12">
        <mdrater :value.sync="star" slot="value"></mdratestar>
        </div>
        
        <div class="col-lg-12 col-md-12">
          <mdalert :show.sync="showAlert1" :text.sync="title" :type="type1" :hide.sync="showColse"></mdalert>
          <mdalert :show.sync="showAlert" :text.sync="title" :type="type2" :hide.sync="showColse2"></mdalert>
          <mdalert :show.sync="showAlert3" :text.sync="title" :type="type3" :hide.sync="showColse"></mdalert>
          <mdalert :show.sync="showAlert" :text.sync="title" :type="type4" :hide.sync="showColse2"></mdalert>
        </div>
        <div class="col-lg-12 col-md-12"> 
          <!-- <countdown slot="value" :time="time" :start="start" :onfinished="finishSend" v-show="start"></countdown> -->
          <button @click="finishSend" v-if="start">stop</button>
          <div v-else>
          <button @click="startSend" >start</button>
          </div>
        </div>
        <div class="col-lg-12 col-md-12">
          <pagination size="lg" variant="primary" :total-rows="100" 
            :current-page="currentPageVariable" :per-page="10">
            </pagination>
        </div>
      </div>
    </div>
  </template>
  <script>
    import mdinput from './../components/form/input.vue';
    import mdradio from './../components/form/radio.vue';
    import mdcheckbox from './../components/form/checkbox.vue';
    import mdselect from './../components/form/select.vue';
    import mdtextarea from './../components/form/textarea.vue';
    import mdcounter from './../components/form/counter.vue';
    import mdsearch from './../components/form/search.vue';
    import mdverifycode from './../components/verifycode.vue';
    import mdrater from './../components/form/rater.vue';
    import mdalert from './../components/alert.vue';
    import countdown from './../components/form/countdown.vue';
    import pagination from './../components/pagination.vue';
    export default {
      components: {
        mdinput,
        mdradio,
        mdcheckbox,
        mdselect,
        mdtextarea,
        mdcounter,
        mdsearch,
        mdverifycode,
        mdrater,
        mdalert,
        countdown,
        pagination
      },
      data() {
        return {
          firstName: 'Tao',
          lastName: '',
          first: 'FirstName',
          radio: 'green',
          textarea:'请输入文本内容',
          checkbox: {
            basketball: true,
            football: false
          },
          selected: null,
          options: ['foo', 'bar', 'baz'],
          choose:'choosing',
          counter:1,
          vertial:'vertial',
          result:false,
          searchvalue:null,
          star:1,
          showAlert:true,
          showAlert1:true,
          showAlert3:true,
          title:'Well done! You successfully read this important alert message.',
          type1:'warning',
          type2:'info',
          type3:'success',
          type4:'danger',
          showColse:false,
          showColse2:true,
          time: 60,       // 验证码限制时间
          start: false,     // 验证码限制是否开启
          currentPageVariable:1,
          swidth: '100%',
          search:'',
          swidthA: '100%',
          searchA:'',
          bgColor:'#ccc',
          bgColorA:'#ccc'
      };
    },
    watch: {
    },
    compiled(){
    },
    ready(){
      this.startSend();
    },
    methods:{
      doVerify(d){
        alert(d);
      },
      search(){
        alert(this.searchvalue);
      },
      // 限制时间结束
      finishSend() {
        this.start = false;
        this.time = 60;
      },
      // 限制时间开始
      startSend(){
        this.start = true;
      },
      //宽度缩小
      narrow(){
        this.swidth = '32%';
        this.bgColor='#fff';
      },
      checkSearch(){
        if(this.seach){
            debugger;
        }else{
          this.swidth='100%';
          this.bgColor='#ccc';
        }
      },
      narrowA(){
        this.swidthA = '32%';
        this.bgColorA='#fff';
      },
      checkSearchA(){
        if(this.seachA){
            debugger;
        }else{
          this.swidthA='100%';
          this.bgColorA='#ccc';
        }
      }
    }
  };
</script>
<style type="text/css">
  .name-f{
    display: inline-block;
    background-color: #ccc;
    color: white;
    min-width: 150px;
  }
  .two-Input{
    width: 100%;
    display: flex;
    flex-flow: row;
    justify-content: space-around;
    height: 100px;
    align-items: center;
  }
   .select-c{
    display: inline-block;
    width: 200px;
    background-color: #ccc;
   }
   .span-O{
    display: inline-block;
    width: 30%;
    height: 40px;
    position: relative;
   }
   .input-O{
    width: 100% !important;
    width: 100%;
    height: 40px;
    z-index: 1;
    border:none;
    outline:none;
   }
   .input-L{
    display: inline-block;
    width: 100%;
    height: 100%;position: absolute;
    right: 0;
    top: 0;
    text-align: left;
    line-height: 40px;
    border:none;
    transition: all 1s;
    background-color: #ccc;
    padding-left: 15px;
   }
   .input-A{
    display: inline-block;
    width: 100%;
    height: 100%;position: absolute;
    right: 0;
    top: 0;
    text-align: left;
    line-height: 40px;
    border:none;
    transition: all 1s;
    background-color: #ccc;
    padding-left: 15px;
   }
  @media (mcol-md-12ax-width: 780px){
    .col-md-12{
      width: 100%;
    }
  }
</style>

