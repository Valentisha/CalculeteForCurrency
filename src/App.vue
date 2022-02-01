<template>
    <div class='base'>
<ul class='base-row'>
<li class="cell1"><div class="content1" >
    <select>
  <option value="" >Доллар</option>
  <option value="">Евро</option>
    </select>
    <br>
    <input v-model='dollars' type='number' placeholder="введите количество"/>
    <!-- <button @click='calculeteDollars' >Посчитать</button> -->
    </div></li>
<li class="cell1"><div class="content2">Рублей:
    <p>{{rublesAmount}}</p>
    </div></li>
</ul>
<p>Если заплатишь {{dollars}} долларов - получишь {{rublesAmount}} рублей по курсу {{dollarsCours}} за доллар</p>
<p>Если заплатишь {{euro}} евро - получишь {{rubles}} рублей по курсу {{euroCours}} за евро</p>
</div>
</template>

<script>
export default {
    data(){
        return {
            rubles: 0,
            dollars: 0,
            euro: 0,
            dollarsCours: 77,
            euroCours: 86,


        }
    },
    methods:{
        calculeteDollars (){
            this.rubles = this.dollarsCours * this.dollars;   
        },
        calculeteEuro(){
            this.rubles = this.euroCours * this.euro;
        },
        
    },
    computed:{
        rublesAmount:{
            get(){
                return this.dollars * this.dollarsCours
            }
        } 
    }

}
</script>

<style >
</style>


