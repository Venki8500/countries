<script setup>
import { onMounted, reactive } from 'vue';

    var state=reactive({
        Countries:[]
    })
    onMounted(function(){
        fetch("https://restcountries.com/v3/all").then(function(res){
            res.json().then(function(data){
                // console.log(data)
                state.Countries=data        
            //  console.log(state.Countries)

            })
        })
    })
</script>
<template>
    <div class="d-flex flex-wrap ">
    <ul v-for="country in state.Countries">
        <div></div>
      <div class="border border-grey rounded shadow  p-2" :style="{marginLeft:'65px',marginTop:'20px'}" >
            <li :style="{listStyle:'none'}"><img :src="country.flags[0]" :style="{width:'350px',height:'200px'}"/></li>
            <b><li :style="{listStyle:'none'}">Country Name : {{ country.name.common }}</li></b>
            <b><li :style="{listStyle:'none'}">Country Population : {{ country.population }}</li></b>
            <b><li :style="{listStyle:'none'}">Country Region : {{ country.region }}</li></b>
            <b><li :style="{listStyle:'none'}">Country Capital : {{ country.capital }}</li></b>
            
        </div>
    </ul>
</div>

</template>