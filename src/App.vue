<template>
  <div id="app" class="container">
    <h1 class="text-center"> {{emittedValue}} </h1>
    <h3 class="text-center"> </h3> 

    <div class="text-center">
    <img class="img-responsive" style="margin:0 auto;" src="./assets/logo.png">
    </div>
    

    
    <div class="row">

      <div class="col-md-12 text-center">
       <BtnTest @BroadCasting="EventHandler($event)"/>

      </div>

    </div>

  </div>
</template>

<script>
import BtnTest from './components/ButtonTest'

export default {
  name: 'App',
  data() {
     return {emittedValue : ""}

  },
  components: {
    BtnTest
  },
  methods:{
      EventHandler(event)
      {
        alert(event);
        this.emittedValue = event;
      }

  }
}
</script>

<!--<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>-->
