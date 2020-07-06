<template>
  <div id='App'>
     <img src="../public/img/hit2.png" />
     <br>
     <button @click="textMk">Текст</button>
     <button @click="textStop">Стоп</button>
     <button @click="test">test</button>
     <br>
     <input v-model="redTextOriginal" v-show="!textShow">
      <marquee id='redTextR' class='redText' direction="right" v-show="runTextFlag" > 
          {{redText}}
      </marquee>

      <div id='redTextS' class='redText' v-show="textStopFlag" > 
          {{redText}}
      </div>

   <br>
    <div id="demo3" class='redText9' >Here’s flowing clockwise.</div>
    <br>

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
      circle:'',
      radiusSetFlag:false,
      circleType:null
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
      this.textStopFlag=false;
      this.circle.destroy.bind(this.circle)

    },
    textStop() {
      this.textStopFlag=true;
      new CircleType(document.getElementById('demo3')).radius(3200);

      //this.circleType.destroy();
      //if (!this.radiusSetFlag) {
        setTimeout(() => {
           this.circleType = new CircleType(document.getElementById('redTextS')).radius(3200);
          }, 1
        );
        this.radiusSetFlag=1;
      //}
      

    },
    test(){
      //new CircleType(document.getElementById('redTextR')).radius(3200);
      this.circleType.destroy();

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



</style>