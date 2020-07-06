<template>
  <div id='App'>
     <img src="../public/img/hit2.png" />
     <br>
     <button @click="textMk">Текст</button>
     <button @click="textStop">Стоп</button>
     <br>
     <input v-model="redTextOriginal" v-show="!textShow">
      <marquee id='redTextR' class='redText' direction="right" v-show="runTextFlag" > 
          {{redText}}
      </marquee>

      <h2 id='redTextS' class='redText' v-show="textStopFlag" > 
          {{redText}}
      </h2>

   <br>
    <div id="demo3"  >Here’s {{redTextOriginal}} flowing clockwise.</div>
    <br>


<span id="curved">Текст располагается по окружности</span>
<span id="curved2">Пример текста располагающегося по кругу</span>


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
      textShow:false,
      leftStart:750,
      textStopFlag:false,
      circle:''
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
      //new CircleType(document.getElementById('demo3')).radius(3200);
      return
    },
  methods:{
    textMk() {
      this.textShow= !this.textShow;
      this.textStopFlag=false;
      this.circle.destroy.bind(this.circle)
    },
    textStop() {
      this.textStopFlag=true;
      this.redTextOriginal+='2';

    $(document).ready(function () {
        $('#curved').elipText({radius: 220});
        $('#curved2').elipText({radius: 160, dir:-1});
    });


      //this.circle=new CircleType(document.getElementById('redTextS'));
      //this.circle.radius(3200);
      //Circle.radius(3200);

      //new CircleType(document.getElementById('redTextS')).radius(3200);
      //new CircleType(document.getElementById('redTextS')).radius(300);

    }

  }
  
 
}
</script>

<style>
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
  background: url("../public/img/fon1.jpg") no-repeat;
  background-size: 100% Auto;
  color: #fff;
  font-family: arial;
  font-size: 120%;
  text-shadow: 5px 5px 5px #555;
  text-align: center;
}

.circle {
  position: relative;
  width: 200px;
  height: 200px;
  border-radius: 50%;
  background: white;
  border: 10px solid burlywood;
  text-align: center;
  line-height: 200px;
  font-size: 22px;
}

span {
  display: inline-block;
  width: 25px;
  position: absolute;
  transform: translate(-12.5px,0px)rotate(var(--rot)) translate(0,-105px)
}


</style>