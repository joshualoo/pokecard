<template>
  <div id="app">
      <Header/>
      <Data/>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Data from './components/Data.vue'
import 'bootstrap/dist/css/bootstrap.css';
import 'animate.css';

let WebFont = require('webfontloader');

WebFont.load({
  google:{
    families :['Anton' , 'IBM Plex Mono']
  }
});

export default {
  name: 'app',
  components: {
    Header,
    Data
  }
  
}
</script>

<style>
#app {
  font-family: 'IBM Plex Mono', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  background-image: linear-gradient(120deg, #fdfbfb 0%, #ebedee 100%);
  padding-bottom:100px;
}
ul{
  padding:0;
}
li{
  list-style:none;
}
.welcome-msg{
  text-align:center;
  padding:0px 0 10px;
}
</style>
