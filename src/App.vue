<template>
  <div id='App' :class="{fon1:isFon1, fon2:isFon2, fon3:isFon3}" >
     
     <img :src="mainImg" />
     <br>
     <button @click="textMk">{{btnTextName}}</button>
     <button id="btnView" @click="textStop" v-show="textShow" >{{btnTextStopName}}</button>
     <button id="btnChangeBG" @click="changeBG">Next backGR </button>
     <button id="btnChangeMainImg" @click="changeMainImg">Next set</button>
     <br>
     <input id="inputText" v-model="redTextOriginal" v-show="!textShow">

      <marquee id='redTextR' class='redText' direction="right" v-show="runTextFlag" > 
          {{redText}}
      </marquee>

      <div id='redTextS' class='redText' v-show="textStopFlag" > 
          {{redText}}
      </div>





  </div>
</template>



<script>
/* eslint-disable no-unused-vars */

import CircleType from '../node_modules/circletype'

export default {
  name: 'Math',
  data() {
    return {
      redTextOriginal:'привет друзья ',
      textShow:true,
      leftStart:750,
      textStopFlag:false,
      circle:'',
      radiusSetFlag:false,
      circleType:null,
      curBG:0,
      imgBG: ['url("./img/fon1.jpg")  no-repeat ','url("./img/fon4.jpg") no-repeat','url("./img/fon3.jpg") no-repeat'],
      curFon:'',
      testColor2:'3px solid green',
      mainImg:'./img/hit3.png',
      BG: {
        background:'url("./img/fon2.jpg") no-repeat',
        backgroundSize: '100%'
      },
      isFon1:false,
      isFon2:true,
      isFon3:false,
      isFon4:false,

      btnTextName:'New Text',
      btnTextStopName:'View'

    }
  },
  computed: {
      redText(){
        return this.redTextOriginal;
      },
      runTextFlag(){
        return this.textShow && !this.textStopFlag;
      }
  },
  created: function(){
      return
    },
  methods:{
    textMk() {
      this.textShow= !this.textShow;
      if (this.textShow)
        this.btnTextName='New Text'
      else
        this.btnTextName='Start';
      this.textStopFlag=false;
      this.circle.destroy.bind(this.circle)

    },
    textStop() {
      this.textStopFlag=!this.textStopFlag;
      if (this.textStopFlag)
        this.btnTextStopName='Start'
      else
        this.btnTextStopName='View'
      //new CircleType(document.getElementById('demo3')).radius(3200);

      //this.circleType.destroy();
      //if (!this.radiusSetFlag) {
        document.getElementById('redTextS').innerHTML=this.redText;
        setTimeout(() => {
           this.circleType = new CircleType(document.getElementById('redTextS')).radius(3700);
          }, 1
        );
        this.radiusSetFlag=1;
      //}
      

    },
    changeBG(){
      //new CircleType(document.getElementById('redTextR')).radius(3200);
      this.curBG++;
      if (this.curBG>2) {
        this.curBG=0;
      }
      this.curFon=this.imgBG[this.curBG];
      this.BG.background=this.curFon;

      this.isFon1=false;
      this.isFon2=false;
      this.isFon3=false;
      this.isFon4=false;
      if (this.curBG==0)
        this.isFon1=true
      else if (this.curBG==1)
        this.isFon2=true
      else if (this.curBG==2)
        this.isFon3=true;
      else if (this.curBG==3)
        this.isFon4=true;


    },
    changeMainImg() {
      if (this.mainImg=='./img/hit3.png') {
        this.mainImg='./img/hit2.png'
      }
      else {
        this.mainImg='./img/hit3.png'
      }
    }

  }
  
 
}
</script>

<style>
#btnChangeBG {
  position:absolute;
  left: 70%;
  top:20%;
}

#btnChangeMainImg {
  position:absolute;
  left: 70%;
  top:30%;

}

#btnView {
  position:relative;
  top:7px;
}

#DT {
  background: hotpink;
  position:absolute;
  left: 50%;
  top: 50%;
  width: 200px;
  height: 50px;
  transform: rotate(15deg);
  transform-origin: center center;
}


@font-face {
  font-family: mel;
  src: url("../fonts/mel.woff2") format("woff2") ;
}

.trText-enter-active {
  transition: opacity 1.5s;
}

.trText-enter {
  opacity: 0;
}

.trText-move {
  transition: transform 3s;
}

.redText {
  color:red;
  z-index: 10;
  text-shadow: none;
  position: absolute;
  font-weight: bold;
  font-size: 130%;
  text-transform: uppercase;
  top:353px;
  left:39.5%;
  width:410px;
  overflow:hidden;
  margin: 0 auto;
  white-space: nowrap;
  padding-right: -100px;
  box-sizing: border-box;
}


body {
  /*background: url("../public/img/fon1.jpg") no-repeat; */
  background-size: 100% Auto;
  color: #fff;
  font-family: arial;
  font-size: 120%;
  text-shadow: 5px 5px 5px #555;
  text-align: center;
}

.fon1 {
  background: url("../public/img/fon1.jpg") ; 
  background-size: 100% Auto;
}
 
.fon2 {
  background: url("../public/img/fon2.png") ; 
  background-size: 100% Auto;
}

.fon3 {
  background: url("../public/img/fon3.png") ; 
  background-size: 100% Auto;
}

.fon4 {
  background: url("../public/img/fon4.jpg") ; 
  background-size: 100% Auto;
}

button {
display: inline-block;
font-size: 1.1em;
height: 50px;
width:90px;
text-decoration:none;
text-align:center;
font: bold 14px arial;
text-transform: uppercase;
padding: 10px 15px;
margin: 20px 20px;
color: #ccc;
background-color: #555;
background-image: linear-gradient(top, #888 0%, #555 100%);
background-image: -webkit-gradient(linear, left top, left bottom, color-stop(0, #888), color-stop(1, #555));
background-image: -moz-linear-gradient(top, #888 0%, #555 100%);
background-image: -o-linear-gradient(top, #888 0%, #555 100%);
border: none;
border-radius: 3px;
text-shadow: 0px -1px 0px #000;
box-shadow: 0px 1px 0px #666,0px 5px 0px #444,0px 6px 6px rgba(0, 0, 0, .6);
-webkit-transition: ease .15s all;
-moz-transition: ease .15s all;
-o-transition: ease .15s all;
transition: ease .15s all;
-webkit-animation: none;
 -moz-animation: none;
 -o-animation: none;
  animation: none;
}
button:hover{
-webkit-animation: linear 1.2s light infinite;
-moz-animation: linear 1.2s light infinite;
-o-animation: linear 1.2s light infinite;
animation: linear 1.2s light infinite;
}
@-webkit-keyframes light{
0%   { color: #ddd; text-shadow: 0px -1px 0px #000; }
50%   { color: #fff; text-shadow: 0px -1px 0px #444, 0px 0px 5px #ffd, 0px 0px 8px #fff; }
100% { color: #ddd; text-shadow: 0px -1px 0px #000; }
}
@-moz-keyframes light{
0%   { color: #ddd; text-shadow: 0px -1px 0px #000; }
50%   { color: #fff; text-shadow: 0px -1px 0px #444, 0px 0px 5px #ffd, 0px 0px 8px #fff; }
100% { color: #ddd; text-shadow: 0px -1px 0px #000; }
}
@-o-keyframes light{
0%   { color: #ddd; text-shadow: 0px -1px 0px #000; }
50%   { color: #fff; text-shadow: 0px -1px 0px #444, 0px 0px 5px #ffd, 0px 0px 8px #fff; }
100% { color: #ddd; text-shadow: 0px -1px 0px #000; }
}
@keyframes light{
0%   { color: #ddd; text-shadow: 0px -1px 0px #000; }
50%   { color: #fff; text-shadow: 0px -1px 0px #444, 0px 0px 5px #ffd, 0px 0px 8px #fff; }
100% { color: #ddd; text-shadow: 0px -1px 0px #000; }
}



</style>