<template>
  <div id="screen">
    <div id="upper">
      <img id="pic" :src="url">
      <div id="right">
        <div id="name"> {{ name.toUpperCase() }} </div>
        <div id="category"> {{ category }} </div>
        <div id="height">HT: {{ height }} m</div>
        <div id="weight">WT: {{ weight }} kg</div>
      </div>
    </div>
    <div id="description">{{ description }}</div>
  </div>
</template>

<script>
export default {
  name: 'PokeScreen',
  props: {
    url: String,
    name: String,
    category: String,
    height: String,
    weight: String,
    description: String
  }
}
</script>

<style scoped>
#screen {
  border: inset 10px #F0F000;
  background-color: #FFFFFF;
  height: 150px;
  width: 180px;
}
#pic {
  height: 50px;
  width: 50px;
}
#upper {
  display: flex;
}
#right {
  font-size: 10px;
  margin: 0;
}
#pic {
  margin: 10px;
}
#description {
  font-size: 11px;
  margin: 0 10px;
  word-wrap: break-word;
}
</style>
