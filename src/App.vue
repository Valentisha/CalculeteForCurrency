<template>
    <div class='base'>
<ul class='base-row'>
    <li class="cell1"><div class="content2">Биткоинов:
     <input v-model='btc' type='number' placeholder="введите количество"/>
    </div></li>
<li class="cell1"><div class="content1" >
    <select v-model="current"> 
  <option v-for="(rate, index) in exchangeRates" v-bind:key="index" :value='index'> {{rate.name}}</option>
    </select>
    
    <button @click="changeCourse(exchangeRates[current].value)" v-if="current">Посчитать</button>
    
    <p>Сумма:{{sum}}</p>
    <!-- <button @click='calculeteDollars' >Посчитать</button> -->
    </div></li>

</ul>
<div v-if="current && exchangeRates" > 
    {{exchangeRates[current].value}} 
    </div>
<!-- {{exchangeRates}} -->
<!-- <div v-for="(rate, index) in exchangeRates" v-bind:key="index">
    {{rate.name}} 
    {{rate.value}}
    </div> -->
<HelloWorld/>  

</div>

</template>

<script>
import HelloWorld from './components/HelloWorld.vue';
import axios from 'axios';
console.log(HelloWorld)
export default {
    mounted(){
        this.$nextTick(()=>{
            const self = this;
            axios.get('https://api.coingecko.com/api/v3/exchange_rates')
                .then(function (response) {
                    (response.data.rates);
                    self.exchangeRates = response.data.rates;
                    // console.log(self);
                })
                .catch(function (error) {
                    console.log(error);
                });
        })
    },
    components: {
        HelloWorld
    },
    data(){
        return {
            btc: 0,
            cours: 50,
            exchangeRates: {},
            current: undefined,

        }
    },
    methods:{
       changeCourse(newCourse){
           this.cours = newCourse;
       }
    },
    computed:{
        sum:{
            get(){
                return this.btc * this.cours
            }
        } 
    }

}
</script>

<style >
</style>


