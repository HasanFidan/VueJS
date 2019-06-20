<template>
  <div id="app" class="container">
    <h1 class="text-center"> {{emittedValue}} </h1>
    <h3 class="text-center"> </h3> 

    <div class="text-center">
    <img class="img-responsive" style="margin:0 auto;" src="./assets/logo.png">
    </div>
  
    <div class="row">

      <div class="col-md-12 text-center">
       <BtnTest @BroadCasting="EventHandler"/>
       <History :historyList="historyList" />

      </div>

    </div>

  </div>
</template>

<script>
import BtnTest from './components/ButtonTest'
import History from './components/History'

export default {
  name: 'App',
  data() {
     return {emittedValue : "",historyList : []}

  },
  components: {
    BtnTest,History
  },
  methods:{
      EventHandler(event)
      {
        this.emittedValue = event;
        this.historyList.push(this.emittedValue);
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
