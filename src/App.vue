<template>
  <MagickBall/>
</template>

<script>
import MagickBall from './components/MagickBall.vue'

export default {
  name: 'App',
  components: {
    MagickBall
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>
