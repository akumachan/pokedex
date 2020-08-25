<template>
  <div id="buttons">
    <div id="indicator">
      Push a button below!
    </div>
    <div id="upper-buttons">
      <button class="poke-button" @click="select('pikachu')"></button>
      <button class="poke-button" @click="select('exeggutor')"></button>
      <button class="poke-button" @click="select('bulbasaur')"></button>
      <button class="poke-button" @click="select('mewtwo')"></button>
      <button class="poke-button" @click="select('diglett')"></button>
    </div>
    <div id="lower-buttons">
      <button class="poke-button" @click="select('machoke')"></button>
      <button class="poke-button" @click="select('rhydon')"></button>
      <button class="poke-button" @click="select('kadabra')"></button>
      <button class="poke-button" @click="select('magikarp')"></button>
      <button class="poke-button" @click="select('lickitung')"></button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'SelectButtons',
  methods: {
    select: function(name) {
      this.$emit('select', name)
    }
  }
}
</script>

<style scoped>
div#buttons {
  display:flex;
  flex-direction: column;
  align-content: center;
}
div#indicator {
  text-align: center;
  background-color: forestgreen;
  color: darkslategray;
  border: inset 5px darkslategray;
  margin: 5px;
}
div#upper-buttons, div#lower-buttons {
  display: flex;
  justify-content: center;
}

button.poke-button {
  height: 35px;
  width: 35px;
  padding: 20px;
  background-color: lightblue;
  border: outset 10px blue;
}
button.poke-button:active {
  background-color: skyblue;
  border: inset 10px blue;
}
button.poke-button:focus {
  outline: 0;
}
</style>