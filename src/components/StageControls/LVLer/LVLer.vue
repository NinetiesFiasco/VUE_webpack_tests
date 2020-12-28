<template>
  <div id='Control'>
    <input type='button' value='<<' @click="val= parseInt(val) - 0.1" />
    <input v-bind:value="val" />
    <input type='button' value='>>' @click="val= parseInt(val) + 0.1" />
  </div>
</template>

<script>
export default {
  name: 'Controls',
  data() {
    return {
      val: 0
    }
  }
}
</script>

<style>
#Control {
  outline: 1px solid black;
}
</style>