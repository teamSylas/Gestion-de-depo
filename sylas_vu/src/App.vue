<template>
  <div id="app">
    <h1> Gestion de Ficher et Analyse d'Image </h1>
    <img alt="Vue logo" src="./assets/cloud.jpg">
    <Uplowdfil msg="The Cloud computing"/>
    <!--<Uplowdfil/>-->
    <br>
    <br>
    <Listefile/>
    <br>
   <!-- <Detect/>-->
  </div>
</template>

<script>
//import HelloWorld from './components/HelloWorld.vue'
import Uplowdfil from './components/Uplowdfil.vue'
import Listefile from './components/Listefile.vue'
//import Detect from './components/Detect.vue'
export default {
  name: 'app',
  components: {
    //HelloWorld,
    Uplowdfil,
    Listefile,
  //  Detect
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

img{
  padding: 20px;
  width:400px
  
}
</style>
