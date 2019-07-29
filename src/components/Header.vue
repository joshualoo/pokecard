<template>

<nav class="navbar animated fadeIn">
  <span class="navbar-text">
              <p class = "used">used with:</p>
              <img class = "logo" alt="logo" v-bind:src = "logo">
    </span>
        </nav>
</template>

<script>
export default {
    name: 'Header',
    data(){
        return{
            logo: require('../assets/pokeapi.png'),
        }
    }
}
</script>

<style scoped>
    .logo{
        width:150px;
    }
    .used{
        display:block;
        margin-bottom:0px;
    }
</style>
    
