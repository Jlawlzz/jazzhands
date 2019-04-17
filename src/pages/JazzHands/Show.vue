<template>
  <div class="container">
    <div id="background"></div>
    <h1>plz come back later</h1>
  </div>
</template>

<script>
export default {
  name: 'Jazzhands',
  data () {
    return {
      sickgifsrc: '/rainblow.webp'
    }
  },
  mounted () {
    let isOpaque = true

    setInterval(() => {
      document.getElementById('background').style.opacity = isOpaque ? .3 : .6
      isOpaque = !isOpaque
    }, 5000)
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped type="text/scss">
.container {
    display: flex;
    flex-direction: row;
    width: 100vw;
    height: calc(100vh - 60px);
    align-items: center;
    justify-content: center;
}
h1 {
  font-size: 150px;
  z-index: 1;
}
#background {
  z-index: 0;
  position: absolute;
  flex-direction: row;
  width: 100vw;
  height: calc(100vh - 60px);
  background-image: url("/rainblow.webp");
  transition: opacity 5s;
  opacity: .5;
}
</style>
