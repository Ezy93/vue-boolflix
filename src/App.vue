<template>
  <div id="app">
    <IndexHeader/>
    <IndexMain/>
  </div>
</template>

<script>
import IndexHeader from './components/IndexHeader.vue';
import IndexMain from './components/IndexMain.vue'
import './scss/style.scss'

export default {
  name: 'App',
  components: {
    IndexHeader,
    IndexMain,
  }
}
</script>

<style lang="scss" scoped>

</style>
