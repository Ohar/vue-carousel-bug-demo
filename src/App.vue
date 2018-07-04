<template>
  <div id="app">
    <CarouselDemo/>
  </div>
</template>

<script>
import CarouselDemo from './components/CarouselDemo'

export default {
  name: 'App',
  components: {
    CarouselDemo
  }
}
</script>

<style>
#app {
  width: 1170px;
  margin: 0 auto;
}
</style>
