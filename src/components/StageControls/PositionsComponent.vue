<template>
  <div>
    <div id="myEl" ref="bigD" @click="getPos" @mousedown="mouseDown" @mouseup="mouseUp" @mousemove="thatMouseMove">
      Делички<br/>
      <div class="values">
        <span>Left:   {{left}}  </span><br/>
        <span>Top:    {{top}}   </span><br/>
        <span>ClickX: {{clickX}}</span><br/>
        <span>ClickY: {{clickY}}</span><br/>
        <span>Width:  {{width}} </span><br/>
        <span>Height: {{height}}</span><br/>
        <span>ThatMoveX:  {{thatMoveX}} </span><br/>
        <span>ThatMoveY:  {{thatMoveY}} </span><br/>
        <span>SmartMoveX: {{smartMoveX}} </span><br/>
        <span>SmartMoveY: {{smartMoveY}} </span><br/>
        <span></span><br/>
      </div>  
      <div>
        {{action}}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      left: 0,
      top: 0,
      clickX: 0,
      clickY: 0,
      width: 0,
      height: 0,
      thatMoveX: 0,
      thatMoveY: 0,
      smartMoveX: 0,
      smartMoveY: 0,
      action: "ppc"
    }
  },
  methods: {
    getPos: function(e) {
      this.clickX = e.clientX
      this.clickY = e.clientY
    },
    getStaticVals: function(){
      this.left = this.$refs.bigD.getBoundingClientRect().left
      this.top = this.$refs.bigD.getBoundingClientRect().top+document.body.scrollTop
      this.width = this.$refs.bigD.clientWidth
      this.height = this.$refs.bigD.clientHeight
    },
    setThatMouseCoords: function(e){
      this.thatMoveX = e.clientX
      this.thatMoveY = e.clientY
    },
    thatMouseMove: function(e) {
      this.setThatMouseCoords(e)
    },    
    setSmartMouseMove: function(e) {

      // нада подумать как грамотно расчитывать свойство TOP
      let x=e.clientX,y=e.clientY,
        right = this.left+this.width,
        top = this.$refs.bigD.getBoundingClientRect().top-document.body.scrollTop,
        bottom = top+this.height
      
      if (x<this.left) x = this.left
      if (x>right) x = right
      if (y<top) y = top
      if (y>bottom) y = bottom

      this.smartMoveX = x
      this.smartMoveY = y
    },
    mouseUpHandler: function(){
      window.removeEventListener("mousemove",this.setSmartMouseMove)
      window.removeEventListener("mouseup",this.mouseUpHandler)
    },
    mouseDown: function(e) {
      //this.action = 'down'
      this.setSmartMouseMove(e)      
      window.addEventListener("mousemove",this.setSmartMouseMove)
      window.addEventListener("mouseup",this.mouseUpHandler)
    },   
    mouseUp: function(e) {
      //this.action = 'up'      
    }
  },
  mounted() {
    this.getStaticVals()
  },  
  name: 'PositionsComponent'
}
</script>

<style scoped>
#myEl {
  width: 600px;
  height: 500px;
  background: lightgrey;
}
.values {
  text-align: left;
}
</style>