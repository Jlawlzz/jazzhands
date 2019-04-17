<template>
  <div class="container" v-on:click="registerClick">
    <div id="background"></div>
    <h1>{{ scripts[clicks%scripts.length] }}</h1>
  </div>
</template>

<script>
export default {
  name: 'Jazzhands',
  data () {
    return {
      sickgifsrc: '/rainblow.webp',
      scripts: [
        'plz come back later',
        'please, im begging you',
        'come back later',
        'oh god why are you clicking',
        'just...',
        'come back later?',
        'PLEASE',
        'OH GAWD WHY, PLEASE JUST COME LATER',
        'IT HURTS',
        'IT BURNS, THE CLICKING BURNS MY SKIN',
        'ALL THE SUNSCREEN IN THE WORLD WONT FIX THIS',
        'MYYYY LEEEEEE...',
        '...EEEEE...',
        '...EGGSSSss',
        'oh jezus i cant feel my legs',
        'this is on you',
        'there is nothing left here for you',
        'just my pain and suffering',
        'ok but seriously all joking aside there is nothing here'
      ],
      clicks: 0,
    }
  },
  mounted () {
    let isOpaque = true

    setInterval(() => {
      document.getElementById('background').style.opacity = isOpaque ? .3 : .6
      isOpaque = !isOpaque
    }, 5000)
  },
  methods: {
    registerClick() {
      this.clicks += 1
    }
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
h1 {
  font-size: 150px;
  z-index: 1;
}
@media only screen and (max-width: 400px) {
  h1 {
    font-size: 60px;
  }
}
</style>
