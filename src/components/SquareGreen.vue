<template>
    <div :class="{'little-square': true , 'switchToActive': isActive}"
         :style="'top:' + coordinates.y + 'px;' + 'left:' + coordinates.x + 'px;'" ></div>
</template>

<script>
export default { 
  data(){
    return{
    
    }
  },
  props: ['coordinates', 'isActive'],
  methods: {
     
  }
  }
</script>


<style>
.switchToActive{
    border: 5px solid rgb(177, 29, 157);
    box-sizing: border-box
  }
  
</style>