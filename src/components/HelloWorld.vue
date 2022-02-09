<template>
<div>
  <div class="square">

    <SquareGreen  :coordinates ='allsquare.square1' :isActive='(activeSquare === allsquare.square1.name)' @click='switchToActive(allsquare.square1.name)'/>
    <SquareGreen  :coordinates ='allsquare.square2' :isActive='(activeSquare === allsquare.square2.name)' @click='switchToActive(allsquare.square2.name)'/>
    <!-- <div class="little-square-second"
         :style="'bottom:' + topsquare + 'px;' + 'right:' + leftsquare + 'px;'"></div> -->
  </div>
  <fieldset :disabled="!Boolean(activeSquare)" >
  <button @click='right'>→</button>
  <button @click='left'>←</button>
  <button @click="up">↑</button>
  <button @click="down">↓</button>
  </fieldset>
  Активный квадрат: {{activeSquare}}
</div>
</template>

<script>
import SquareGreen from './SquareGreen.vue'


export default { 
  data(){
    return{
    allsquare: { 
                square1: {x: 0, y: 0, name: 'square1'}, 
                square2: {x: 300, y: 300, name: 'square2'}
                 },
    activeSquare: null,
    
    }
  },
  components: {
    SquareGreen,
  },
  methods: {

    up(){
      if(this.allsquare[this.activeSquare].y >= 100){
      
      this.allsquare[this.activeSquare].y  = this.allsquare[this.activeSquare].y  - 100
      } 

    },
    down(){
      if( this.allsquare[this.activeSquare].y <= 200){

      this.allsquare[this.activeSquare].y  = this.allsquare[this.activeSquare].y  + 100}
    },
    left(){
      if(this.allsquare[this.activeSquare].x >= 100){
      this.allsquare[this.activeSquare].x = this.allsquare[this.activeSquare].x - 100}
    },
    right(){
      if (this.allsquare[this.activeSquare].x <= 200){
      this.allsquare[this.activeSquare].x = this.allsquare[this.activeSquare].x + 100} 
    },
    reloadgreen(){
      this.leftsquare = 0,
      this.topsquare = 0
    },
    switchToActive(name){
      // this.toBorderForSquare = !this.toBorderForSquare
      // this.toBorderForSquare2 = !this.toBorderForSquare2
      this.activeSquare = name
    },
   
    

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
