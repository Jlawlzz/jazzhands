<template>
  <div id="app">
    <Header/>    
    <JazzHands/>
  </div>
</template>

<script>
import Header from './components/Header'
import JazzHands from './pages/JazzHands/Show'

export default {
  name: 'app',
  components: {
    Header,
    JazzHands,
  }
}
</script>

<style>
body {
  margin: 0;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
