<template>
  <div class="container" v-on:click="registerClick">
    <div id="background" v-bind:style="backgroundStyle"></div>
    <h1 v-bind:style="textStyle">
      {{ scripts[scriptsIdx%scripts.length] }}
    </h1>
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
      themes: [
        {
          background: '1_background_light.webp',
          textColor: '#2c3e50',
          textOutline: 'transparent',
          opacityHigh: .7,
          opacityLow: .3
        },
        {
          background: '3_background_light.webp',
          textColor: '#2c3e50',
          textOutline: 'transparent',
          opacityHigh: .7,
          opacityLow: .3
        },
        {
          background: '4_background.gif',
          textColor: '#2c3e50',
          textOutline: 'transparent',
          opacityHigh: .7,
          opacityLow: .3
        },
      ],
      scriptsIdx: 0,
      backgroundIdx: 0,
      isOpaque: true,
      selectedTheme: null,
      backgroundStyle: {},
      textStyle: {}
    }
  },
  mounted () {
    this.selectedTheme = this.themes[this.backgroundIdx]
    this.setDefaultTheme()
    this.setThemeInterval()
  },
  methods: {
    setDefaultTheme () {
      this.textStyle = {
        color: this.selectedTheme.textColor
      }
      this.backgroundStyle = {
        background: `url("${this.selectedTheme.background}")`,
        opacity: this.selectedTheme.opacityLow
      }
    },
    setThemeInterval () {
      let that = this
      setInterval(() => {
        that.backgroundStyle.opacity = that.isOpaque
          ? that.selectedTheme.opacityLow
          : that.selectedTheme.opacityHigh
        that.isOpaque = !that.isOpaque
      }, 5000)
    },
    registerClick () {
      this.scriptsIdx += 1

      if (this.scriptsIdx % this.scripts.length == 0) {
        this.backgroundIdx += 1
        this.selectedTheme = this.themes[this.backgroundIdx % this.themes.length]
        this.updateBackground()
        this.updateText()
      }
    },
    updateBackground () {
      this.backgroundStyle.transition = 'opacity 0s'
      this.backgroundStyle.backgroundImage = `url("${this.selectedTheme.background}")`
      this.backgroundStyle.transition = 'opacity 5s'
    },
    updateText () {
      this.textStyle.color = this.selectedTheme.textColor
      this.textStyle.backgroundColor = this.selectedTheme.textOutline 
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
  /* background-image: url("/rainblow.webp"); */
  transition: opacity 5s;
  opacity: .5;
}
h1 {
  font-size: 150px;
  z-index: 1;
}
@media only screen and (max-width: 1200px) {
  h1 {
    font-size: 100px;
  }
}
@media only screen and (max-width: 400px) {
  h1 {
    font-size: 60px;
  }
}
</style>
