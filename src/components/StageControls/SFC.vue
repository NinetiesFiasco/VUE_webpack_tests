<template>
  <div>
    <div>Tuta</div>
    <p>{{ hello }}</p>
    <h3 v-for="item in todo" :key="item.id" v-on:click="someClick(item.msg)">Id: {{item.id}} msg: {{item.msg}}</h3>
    <div v-on:click="counter = counter + 1">{{ counter }}</div>
    <div class='blueSquare square' @click="isTrue = !isTrue"></div>
    <div class='greenSquare square' v-show="isTrue"></div>
    <div class='yellowSquare square' @click.once="oneTimeClick"></div>
    <div class='purpleSquare square' @click.once="hello = 'uje hellouknul'"></div>
  </div>
</template>

<script>


const someClick = function() {
  alert ('tuta')
}

export default {
  name:"SFC",
  data(){
    return {
      hello: 'Hello world!',
      todo: [
        {id: 1,msg:"one"},
        {id: 2,msg:"two"},
        {id: 3,msg:"three"}
      ],
      counter: 0,
      isTrue: true
    }    
  },
  methods: {
    someClick : function (value) {
      alert(value)
    },
    oneTimeClick : function () {
      alert('Vtoroi raz ne kliknesh ' + this.counter)
    }
  },
  watch: {
    hello: function () {
      alert(this.hello)
    }
  }

}

</script>

<style scoped>
.square {
  display: block;
  width: 15px;
  height: 15px;
}
.blueSquare{
  background: blue;
}
.greenSquare {
  background: green;
}
.yellowSquare {
  background: yellow;
}
.purpleSquare {
  background: purple;
}
</style>