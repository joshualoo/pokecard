<template>
  <div class="container">
    <!-- <pre> {{data.game_indices[0].game_index}} </pre> -->

<div class="poke-card shadow-lg bg-white rounded animated fadeInUp">
    <h3 class = "pokename text-center">#{{data.game_indices[0].game_index}}-{{ data.name | capitalize }}</h3>

    <div class="row">
        <div class="col text-center">   
            <div class="img-container">
                <img class = "poke-img" :src="`${data.sprites.front_default}`">
                <!-- <img class = "poke-img" :src="`${data.sprites.back_default}`"> -->
            </div>

        </div>
        <!-- <span v-if="!isHidden">
            <div class="col">
                <img class = "poke-img" :src="`${data.sprites.front_shiny}`">
                <img class = "poke-img" :src="`${data.sprites.back_shiny}`">
            </div>
        </span> -->
    </div>
    <div class="row">
        <div class="col">    
            <h3>Measurements:</h3>
            <ul class = "vitals">
                <li>Weight: {{data.weight | decimal}} kg</li>
                <li>Height: {{data.height}} cm</li>
            </ul>
            <h3>Stats:</h3>
            <ul class = "stats">
                <li>{{data.stats[0].stat.name | capitalize}} : {{data.stats[0].base_stat}}</li>
                <li>{{data.stats[1].stat.name | capitalize}} : {{data.stats[1].base_stat}}</li>
                <li>{{data.stats[2].stat.name | capitalize}} : {{data.stats[2].base_stat}}</li>
                <li>{{data.stats[3].stat.name | capitalize}} : {{data.stats[3].base_stat}}</li>
                <li>{{data.stats[4].stat.name | capitalize}} : {{data.stats[4].base_stat}}</li>
                <li>{{data.stats[5].stat.name | capitalize}} : {{data.stats[5].base_stat}}</li>
            </ul>
        </div>
        <div class="col">
            <!-- <h3>{{ data.abilities[0].ability.name | capitalize}}</h3>
            <h3>{{ data.abilities[1].ability.name | capitalize}}</h3> -->
            <h3>Abilities:</h3>
            <ul class = 'abilities'>
                <li>{{data.moves[0].move.name | capitalize}}</li>
                <li>{{data.moves[1].move.name | capitalize}}</li>
                <li>{{data.moves[2].move.name | capitalize}}</li>
                <li>{{data.moves[3].move.name | capitalize}}</li>
            </ul>    
        </div>
    </div>
  
    </div>

</div>
</template>

<script>
// install axios to handle fetch better
const axios = require('axios');
let randomPokemon = Math.floor((Math.random() * 200) + 1);

export default {
    name: 'Data',
    props:{
        data : null,
    },  
    methods:{
        render(){
            this.$forceUpdate();
        }
    },
    // only capitalize the first letter of the name 
    filters:{
        capitalize: function(word){
           if (!word) return ''
            word = word.toString()
            return word.charAt(0).toUpperCase() + word.slice(1)
        },
        decimal: function(num){
            if (!num) return ''
            return (num / 10).toFixed(1)
        }
    },
    mounted(){
        axios
            .get('https://pokeapi.co/api/v2/pokemon/' + randomPokemon + '/')
            .then(response =>(this.data = response.data))
        }
    }
    
</script>

<style scoped>
    .container{
        height:100%;
    }
    .col>h3{
        border-bottom: 10px solid darkturquoise;
        width: fit-content;
        -webkit-margin-before-collapse: collapse;
        margin-bottom: 5px;
        margin-top:15px
    }
    .poke-card{
        width:70%;
        margin:0 auto;
        padding:50px 70px;
    }
    .img-container{
        border-radius:50%;
        background-color: rgba(222,222,222,0.5);
        height: 100%;
        width: fit-content;
        margin: 0 auto;
        padding: 5px;
    }
    .poke-img{
        width:250px;
    }
    .pokename{
        font-size:50px;
    }

</style>
