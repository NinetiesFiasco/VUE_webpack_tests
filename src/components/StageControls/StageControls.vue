<template>
  <div id='StageControls'>
    <h3>Мои контрольчики</h3>
    <LVLer v-bind:val="1" />
  </div>
</template>

<script>
import LVLer from './LVLer/LVLer.vue'

export default {
  name: 'StageControls',
  components: {
    LVLer
  },
  props: {},
  data() {
    return {}
  }
}
</script>

<style>
#StageControls {
  width: 400px;
  height: 500px;
  outline: 1px solid black;
}
</style>