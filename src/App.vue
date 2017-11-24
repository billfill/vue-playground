<template>
  <div id="app">
    <smoothyScroll></smoothyScroll>
  </div>
</template>

<script>
import smoothyScroll from './components/smoothy-scroll.vue'
export default {
  name: 'app',
  components: {
    smoothyScroll,
  }
}
</script>

<style lang="scss" scoped>
  #app{
    width: 100%;
    height: 100vh;
    overflow: hidden;
    background-color: #dafae5;
    display: flex;
    justify-content: center;
    align-items: center;
  }

</style>
