<template>
  <div class='content'>
    <div class="activity-lottery-winning">
      <img src="./../assets/image/background.jpg" alt="" class='background'>
      <img src="./../assets/image/topName.png" alt="" class='topName'>
      <div class="main">
        <div id="outercont">
          <div id="outer-cont">
            <div id="outer">
              <img src="./../assets/image/turn.png" width=310>
            </div>
          </div>
          <div id="inner-cont">
            <div id="inner" @click='roate'>
              <img src="./../assets/image/arrowDown.png" alt="" class='arrorDown'>
              <img src="./../assets/image/middleButton1.png">
            </div>
          </div>
        </div>
        <div class="content">

        </div>

      </div>
    </div>
  </div>

</template>

<script type='text/ecmascript-6'>
//  import bus from '../bus.js'
  import { XDialog, XButton, Group, TransferDomDirective as TransferDom } from 'vux'
//  import jQuery from 'jquery'
  import $ from 'jquery'
  import './../assets/jQueryRotate.2.2'

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
        phoneNum  : null,
        rotating : false,
        dataObj :  [0, 45, 90, 135, 180, 225, 270, 315]
      }
    },
    mounted(){
//      var rotating = false;

},
    methods:{
      roate(){
//        let  rotating = false
        let self = this
//        console.log("this.dataObj:",self.dataObj)
//        let dataObj = [0, 45, 90, 135, 180, 225, 270, 315]
        var key = this.getRandom(0, 12);
        console.log(key)
        console.log("self.rotating:",self.rotating)
        !self.rotating && this.rotateFunc(self.dataObj[key], key);
//        console.log('1')

      },
      getRandom (min  , max) {
        //x上限，y下限
        var x = max;
        var y = min;
        if (x < y) {
          x = min;
          y = max;
        }
        var rand = parseInt(Math.random() * (x - y + 1) + y);
        return rand;
      },
      rotateFunc(num, type){
        let self = this
        self.rotating = true;
        console.log('this.rotating:',this.rotating)
        console.log('num',num)
//        console.log('type',type)
        $("#outer").rotate({
          angle: 0,
          duration: 4000,
          animateTo: num + 1440, //1440是我要让指针旋转4圈
          callback: function() {
            self.rotating = false;
            if (type == 0) {
              console.log("恭喜你获得一等奖");
            } else if (type == 4) {
              console.log("恭喜你获得二等奖");
            } else if (type == 8) {
              console.log("恭喜你获得三等奖");
            } else {
              console.log("再接再厉");
            }
          }
        });
      }

      }
  }
</script>

<style lang="less" scoped>
  @import "./../assets/css/close.less";
  @import "./../assets/css/reset.css";
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
  body, div, dl, dt, dd, ul, ol, li, h1, h2, h3, h4, h5, h6, pre, code, form, fieldset, legend, input, textarea, p, blockquote, th, td {
    margin: 0;
    padding: 0;color: #444444;
    font: 14px/1.5 Microsoft YaHei, Helvitica, Verdana, Arial, san-serif;
  }
  /*.activity-lottery-winning{ background: url(./../images/background.jpg) #2a8a00;}*/
  /*.activity-lottery-end{ background: url(http://www.wxapi.cn/index/images/activity/activity-lottery-bg2.jpg) #2a8a00;}*/
  /*.activity-coupon-winning{ background-color:#8d0001;}*/
  /*.activity-coupon-end{ background-color:#8d0001;}*/
  /*.activity-scratch-card-winning{background: url(http://www.wxapi.cn/index/images/activity/activity-scratch-card-bg.jpg) #944f20;}*/
  /*.activity-scratch-card-end{background: url(http://www.wxapi.cn/index/images/activity/activity-scratch-card-bg.jpg) #944f20;}*/
  /*.activity-lottery-winning .main{*/
  /*background: url(http://www.wxapi.cn/index/images/activity/activity-lottery-bg.png) no-repeat top center;*/
  /*}*/

  #outer-cont {
    position: relative;
    width: 100%;
    top: 20px;
    margin-bottom: 30px;/* -moz-transform: rotate(-5deg);
    -webkit-transform: rotate(-5deg);
    -o-transform: rotate(-5deg);
    -ms-transform: rotate(-5deg);
    transform: rotate(-5deg); */
  }
  #inner-cont {
    position: absolute;
    width: 100%;
    top: 2.8rem;
    padding-left: .2rem;
    /* -moz-transform: rotate(-5deg);
    -webkit-transform: rotate(-5deg);
    -o-transform: rotate(-5deg);
    -ms-transform: rotate(-5deg);
    transform: rotate(-5deg); */
  }
  #outer {
    width : 310px;
    max-width: 310px;
    height: 310px;
    margin: 0 auto;
  }
  #inner {
    width : 112px;
    max-width: 112px;
    height: 142px;
    margin: 0 auto;
    cursor: pointer;
  }
  #outer img, #inner img {
    display: block;
    margin: 0 auto;
  }
  .cover{
    width: 320px;
    max-width: 480px;
    margin: 0 auto;
    position: relative;
  }
  .cover img{
    width: 320px;
  }
  #scratchpad,#prize{
    position: absolute;
    width: 150px;
    height: 40px;
    top: 140px;
    left: 105px;
    text-align: center;
    font-size: 20px;
    line-height: 40px;
    color:#333;
  }
  .btn-cont{
    position: absolute;
    bottom: 3px;
    right: 3px;
    display: none;
  }
  .content {
    margin:0px 0 15px 0;
  }
  .banner {
    text-align:center;
  }
  .main{
    position: absolute;
    top: 2rem;
    left : 9%;
  }
  .main img {
    max-width: 105%;
    border: 0 none;

  }
  .arrorDown{
    position: absolute;
    top: -2.5rem;
    padding-left: .7rem;
    height: 2rem;
  }
  .background{
    width : 100%;
  }

  .topName{
    position: absolute;
    top: 0;
    width: 100%;
  }
  .boxcontent {
    margin:1px 15px 15px 15px;
    border-radius: 5px;
    padding: 2px;
    background-color: #FEF8B2;
    -webkit-box-shadow: 0 0 6px rgba(0, 0, 0, 0.5);
    -moz-box-shadow: 0 0 6px rgba(0, 0, 0, 0.5);
    -o-box-shadow: 0 0 6px rgba(0, 0, 0, 0.5);
    box-shadow: 0 0 6px rgba(0, 0, 0, 0.5);
  }
  .boxyellow{
    background-color: #FEF8B2;
  }
  .boxwhite{
    background-color: #ffffff;
  }
  .box {
    border-radius: 5px;
    font-size:14px;
    border: 1px dashed rgba(0, 0, 0, 0.3);
  }
  .box .title-red {
    padding: 0 5px 0px 10px;
    background:url(http://www.wxapi.cn/index/images/activity/title-bg-red.png) no-repeat 0 0;
    border-radius: 3px 3px 3px 0;
    color:#ffffff;
    height:22px;
    margin:-1px;
    /*-moz-text-shadow:0 1px 0 #8d0001;-webkit-text-shadow:0 1px 0 #8d0001;text-shadow:0 1px 0 #8d0001;
    text-shadow:0px 1px 0 #8d0001;*/
  }
  .box .title-orange {
    padding: 0 5px 0px 10px;
    background:url(http://www.wxapi.cn/index/images/activity/title-bg-orange.png) no-repeat 0 0;
    border-radius: 3px 3px 3px 0;
    color:#ffffff;
    height:22px;
    margin:-1px;
    /*-moz-text-shadow:0 1px 0 #8d0001;-webkit-text-shadow:0 1px 0 #8d0001;text-shadow:0 1px 0 #8d0001;
    text-shadow:0px 1px 0 #8d0001;*/
  }
  .box .title-green {
    padding: 0 5px 0px 10px;
    background:url(http://www.wxapi.cn/index/images/activity/title-bg-green.png) no-repeat 0 0;
    border-radius: 3px 3px 3px 0;
    color:#ffffff;
    height:22px;
    margin:-1px;
    /*-moz-text-shadow:0 1px 0 #8d0001;-webkit-text-shadow:0 1px 0 #8d0001;text-shadow:0 1px 0 #8d0001;
    text-shadow:0px 1px 0 #8d0001;*/
  }
  .box .title-brown {
    padding: 0 5px 0px 10px;
    background:url(http://www.wxapi.cn/index/images/activity/title-bg-brown.png) no-repeat 0 0;
    border-radius: 3px 3px 3px 0;
    color:#ffffff;
    height:22px;
    margin:-1px;
    /*-moz-text-shadow:0 1px 0 #8d0001;-webkit-text-shadow:0 1px 0 #8d0001;text-shadow:0 1px 0 #8d0001;
    text-shadow:0px 1px 0 #8d0001;*/
  }
  .box .Detail {
    padding: 15px;
  }
  .red {
    color:red
  }
  .px {
    margin: 0.5em 0;
    position: relative;
    box-shadow: 0 1px 4px rgba(0, 0, 0, 0.3) inset;
    background-color: #FFFFFF;
    border-radius: 0.6em 0.6em 0.6em 0.6em;
    border: 1px solid rgba(0, 0, 0, 0.3);
    color: #333333;
    text-shadow: 0 1px 0 #FFFFFF;
    display: block;
    width: 100%;
    padding:6px 10px;
    font-size: 18px;
    margin:10px 0 0 0;
    font-family:Arial, Helvetica, sans-serif;
  }
  .px:hover {
    border: 1px solid #ff6501;
  }
  .px:focus {
    border: 1px solid #ff6501;
    box-shadow: 0 0 5px #ff6501;
  }
  .px[type="text"] {
    width: 100%;
    box-sizing: border-box;
    -webkit-box-sizing:border-box;
    -moz-box-sizing: border-box;
  }
  .pxbtn {

    background: #ff6501;
    background-image: -webkit-gradient(linear, left top, left bottom, from( #ffa201 ), to( #ff6501 )); /* Saf4+, Chrome */
    background-image: -webkit-linear-gradient( #ffa201 , #ff6501 ); /* Chrome 10+, Saf5.1+ */
    background-image:    -moz-linear-gradient( #ffa201 , #ff6501 ); /* FF3.6 */
    background-image:     -ms-linear-gradient( #ffa201 , #ff6501 ); /* IE10 */
    background-image:      -o-linear-gradient( #ffa201 , #ff6501 ); /* Opera 11.10+ */
    background-image:         linear-gradient( #ffa201 , #ff6501 );
    border: 1px solid #ff6501;
    border-bottom: 1px solid #d35605;
    color: #ffffff;
    font-weight: bold;
    text-shadow: 0 1px 0 #FFFFFF;
    border-radius: 0.6em 0.6em 0.6em 0.6em;
    display: block;
    width: 100%;
    box-shadow: 0 1px 3px rgba(0, 0, 0, 0.5);
    text-overflow: ellipsis;
    white-space: nowrap;
    cursor: pointer;
    text-align: center;
    font-weight: bold;
    text-shadow: 0 0 2px #BE4205;
    font-size: 18px;
    padding:10px;
    margin:10px 0 0 0;
  }
  .pxbtn:visited {
    background-image: -webkit-gradient(linear, left top, left bottom, from( #ffa201 ), to( #ff6501 )); /* Saf4+, Chrome */
    background-image: -webkit-linear-gradient( #ffa201 , #ff6501 ); /* Chrome 10+, Saf5.1+ */
    background-image:    -moz-linear-gradient( #ffa201 , #ff6501 ); /* FF3.6 */
    background-image:     -ms-linear-gradient( #ffa201 , #ff6501 ); /* IE10 */
    background-image:      -o-linear-gradient( #ffa201 , #ff6501 ); /* Opera 11.10+ */
    background-image:         linear-gradient( #ffa201 , #ff6501 );
  }
  .pxbtn:hover {
    background-image: -webkit-gradient(linear, left top, left bottom, from( #ff7f01 ), to( #ff6501 )); /* Saf4+, Chrome */
    background-image: -webkit-linear-gradient( #ff7f01 , #ff6501 ); /* Chrome 10+, Saf5.1+ */
    background-image:    -moz-linear-gradient( #ff7f01 , #ff6501 ); /* FF3.6 */
    background-image:     -ms-linear-gradient( #ff7f01 , #ff6501 ); /* IE10 */
    background-image:      -o-linear-gradient( #ff7f01 , #ff6501 ); /* Opera 11.10+ */
    background-image:         linear-gradient( #ff7f01 , #ff6501 );
  }
  .pxbtn:active {
    background-image: -webkit-gradient(linear, left top, left bottom, from( #ff6501 ), to( #ffa201 )); /* Saf4+, Chrome */
    background-image: -webkit-linear-gradient( #ff6501 , #ffa201 ); /* Chrome 10+, Saf5.1+ */
    background-image:    -moz-linear-gradient( #ff6501 , #ffa201 ); /* FF3.6 */
    background-image:     -ms-linear-gradient( #ff6501 , #ffa201 ); /* IE10 */
    background-image:      -o-linear-gradient( #ff6501 , #ffa201 ); /* Opera 11.10+ */
    background-image:         linear-gradient( #ff6501 , #ffa201 );
    border: 1px solid #ff6501;
    border-top: 1px solid #d35605;
    box-shadow: 0 1px 4px rgba(0, 0, 0, 0.3) inset;
  }
  input::-moz-placeholder, textarea::-moz-placeholder { color: #999;}
</style>
