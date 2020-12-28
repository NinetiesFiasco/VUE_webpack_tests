<template>
  <div id="app">
    <SFC/>
    <StyleTest/>
    <PositionsComponent/>
    <img width="25%" src="./assets/logo.png">
    <HelloWorld/>
    <StageControls/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import StageControls from './components/StageControls/StageControls.vue'
import StyleTest from './components/StyleTest.vue'
import SFC from './components/StageControls/SFC'
import PositionsComponent from './components/StageControls/PositionsComponent'

export default {
  name: 'App',
  components: {
    HelloWorld, StageControls, StyleTest, SFC, PositionsComponent
  }
}
</script>

<style>
#app {
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>