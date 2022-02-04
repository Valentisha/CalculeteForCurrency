<template>
<div>
  <div class="square">
    <div class="little-square" @click='reload' :style="'top:' + topsquare + 'px;' + 'left:' + leftsquare + 'px;'" ></div>
  </div>
  <button @click='right'>→</button>
  <button @click='left'>←</button>
  <button @click="up">↑</button>
  <button @click="down">↓</button>
{{topsquare}}
</div>
</template>

<script>
export default {

    
  data(){
    return{
    leftsquare: 0,
    topsquare : 0,
    }
  },
  methods: {
    up(){

      // if ( this.topsquare - 100 >= 0) {
// ok norm i'm fine blya
      // }

      if(this.topsquare >= 100){
      this.topsquare  = this.topsquare  - 100}
      
    },
    down(){

      console.log(this.topsquare)
      // 300  

      // if (  (this.topsquare + 100 < 400) )  {
        // good
      // } 


      if( this.topsquare <= 200){
      this.topsquare  = this.topsquare  + 100}
    },
    left(){
      if(this.leftsquare >= 100){
      this.leftsquare = this.leftsquare - 100}
    },
    right(){
      if (this.leftsquare <= 200){
      this.leftsquare = this.leftsquare + 100}
    },
    reload(){
      this.leftsquare = 0,
      this.topsquare = 0
    },



    moveRight(leftCoord) {
      return leftCoord + 100;
    }

  }
}
</script>

<style>
 .square{
   position: relative;
   width: 400px;
   height: 400px;
   border: 2px solid green;
}
  .little-square{
    position: absolute;
    left: 0;
    top: 0;
    width: 100px;
    height: 100px;
    background: lawngreen;
    transition: 300ms ease all;
}
</style>
