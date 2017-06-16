<template>
  <div class='content'>
    <img src="./../assets/image/backgroundNew.png" alt="">
    <group class="weui_cells_form inputCode">
      <input placeholder='输入你的手机号' class='box'  v-model="phoneNum">
    </group>
    <!--<flexbox>-->
      <!--<flexbox-item  :span="8" >-->
        <!--<group class="weui_cells_form inputCode">-->
          <!--<input placeholder='输入验证码' class="weui_vcode box">-->
           <!--</input>-->
        <!--</group>-->
      <!--</flexbox-item>-->
      <!--<flexbox-item>-->
          <!--&lt;!&ndash;<x-button style='background-color: #ffbf00'>&ndash;&gt;-->
            <!--<timer-btn type='button' :start='start' @countDown ='start=false' @click.native='sendCode' >-->
            <!--</timer-btn>-->
          <!--&lt;!&ndash;</x-button>&ndash;&gt;-->
      <!--</flexbox-item>-->
    <!--</flexbox>-->

      <x-button style='background-color: #ffbf00;margin: .3rem 5%;width: 90%;'  :title="'hide on clicking mask'" @click.native="sendMessage(phoneNum)"  >
        立即预约领取
      </x-button>


    <div v-transfer-dom style='max-height:4rem;'>
      <x-dialog v-model="showHide0" class="dialog-demo" hide-on-blur >
        <div class="img-box">
          <p style='padding: .6rem;'>领取成功!</p>
          <p>微信关注"爱分趣"公众号查看</p>
          <div class='btn'  type='default '>爱分趣</div>
          <p style='color:#ffbf00;'>长按上方按钮复制微信号</p>
        </div>
        <div @click="showHide0=false">
          <span class="vux-close"></span>
        </div>
      </x-dialog>
    </div>

    <div v-transfer-dom style='max-height:4rem;'>
      <x-dialog v-model="showHide1" class="dialog-demo" hide-on-blur >
          <p style='height: 1rem;text-align: center;line-height: 1rem;'>请输入有效的手机号码！</p>
        <p>微信关注爱分趣公众号查看</p>

        <div @click="showHide1=false">
          <span class="vux-close"></span>
        </div>
      </x-dialog>
    </div>
  </div>

</template>

<script type='text/ecmascript-6'>
//  import bus from '../bus.js'
  import { XDialog, XButton, Group, TransferDomDirective as TransferDom } from 'vux'
  import  $ from 'jquery'


  export default {
    directives: {
      TransferDom
    },
    components: {
      XDialog,
      XButton,
      Group
    },
    data(){
      return {
        start : false,
        show : false,
        showHide0: false,
        showHide1: false,
        phoneNum  : null
      }
    },
    created(){
    },
    methods:{
      sendCode (value) {
        //前面发送ajax请求成功之后调用this.start = true开始短信倒计时
        this.start = true
      },
      sendMessage (phoneNum){
//        console.log("phoneNum:"+JSON.stringify(phoneNum));
//        let phone = parseInt(phoneNum);
        var myreg = /^(((13[0-9]{1})|(15[0-9]{1})|(18[0-9]{1}))+\d{8})$/;
        if(!myreg.test(parseInt(phoneNum))){
            this.show = true;
            this.showHide1 = true;
            return false;
          }else{
            this.showHide0 = true;
          }
        },
      }
  }
</script>

<style lang="less" scoped>
  @import "./../assets/css/close.less";
  .content{
    background: rgb(245, 245, 245);
  }
  img{
    width:100%;
  }
  input{
    border: 0px;
    width: 100%;
  }
  p{
    color: #8e8e8e;
    font-size : .24rem;
  }

  .inputCode{
    margin: 0  .3rem;

  }
  .box{
    margin-top: 0;
    height: 1.4rem;
    line-height: 1rem;
    padding-left: .3rem;
  }
  .btn{
    background-color: #ffbf00;
    margin:.25rem 15%;
    width:70%;
    color:#ffffff;
    height: 1rem;
    line-height: 1rem;
    font-size: .4rem;
  }

  .allcontent{
    width: 100%;
    position:relative;
    animation:myfirst 4s;
    -moz-animation:myfirst 4s; /* Firefox */
    -webkit-animation:myfirst 4s; /* Safari and Chrome */
    -o-animation:myfirst 4s; /* Opera */
  }

  @keyframes myfirst
  {
    0%   { bottom:10rem; right:0px;}
    50%  { bottom:0px; right:0px;}

  }
  @-webkit-keyframes myfirst /* Safari and Chrome */
  {
    0%   { bottom:10rem; right:0px;}
    50%  { bottom:0px; right:0px;}

  }

  ::-webkit-input-placeholder {
    color: #bababa;
    font-size:.4rem;
    padding-left: .3rem;
  }


  .dialog-demo {
  .weui-dialog{
    border-radius: 8px;
    padding-bottom: 8px;
  }
  .dialog-title {
    line-height: 30px;
    color: #666;
  }
  .img-box {
    height: 4rem;
    overflow: hidden;
  }
  .vux-close {
    margin-top: 8px;
    margin-bottom: 8px;
  }
  }
</style>
