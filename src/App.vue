<template>
    <div class='base'>
<ul class='base-row'>
    <li class="cell1"><div class="content2">Биткоинов:
     <input v-model='btc' type='number' placeholder="введите количество"/>
    </div></li>
<li class="cell1"><div class="content1" >
    <!-- <select>
  <option value="" >Доллар</option>
  <option value="">Евро</option>
    </select> -->
    <button @click="changeCourse(100)">Посчитать в долларах</button>
    <button @click="changeCourse(150)">Посчитать в евро</button>
    <p>Сумма:{{sum}}</p>
    <!-- <button @click='calculeteDollars' >Посчитать</button> -->
    </div></li>

</ul>

{{cours}}
</div>
</template>

<script>

import axios from 'axios';

export default {
    mounted(){
        this.$nextTick(()=>{
            this.valya = 55;
            axios.get('https://api.coingecko.com/api/v3/exchange_rates')
                .then(function (response) {
                    console.log(response.data);
                })
                .catch(function (error) {
                    console.log(error);
                });
        })
    },
    data(){
        return {
            btc: 0,
            valya: 0,
            cours: 50,
            
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


