<template>
  <div id="app">
    <PokeScreen
      :url="imgUrl"
      :name="name"
      :category="genus"
      :height="height"
      :weight="weight"
      :description="description"
    />
    <SelectButtons @select="search($event)"></SelectButtons>
  </div>
</template>

<script>
import PokeScreen from './components/PokeScreen.vue'
import SelectButtons from './components/SelectButtons'
import axios from 'axios'

export default {
  name: 'App',
  components: {
    PokeScreen,
    SelectButtons
  },
  data () {
    return {
      name: 'phantom',
      genus: '???',
      height: '???',
      weight: '???',
      imgUrl: require('@/assets/phantom.jpeg'),
      description: '??????????????????????????????',
    }
  },
  methods: {
    search: function(name) {
      const api = 'https://pokeapi.co/api/v2/pokemon/'
      axios.get(`${ api }${ name }`)
          .then((response) => {
            const pokemon = response.data
            this.name = pokemon.name
            this.height = String(pokemon.height / 10)
            this.weight = String(pokemon.weight / 10)
            this.imgUrl = pokemon.sprites.versions['generation-i']['red-blue'].front_gray
            return axios.get(pokemon.species.url)

          }).then((response) => {
            const species = response.data
            this.genus = species.genera.filter((v) => v.language.name === 'en')[0].genus
            this.description = species.flavor_text_entries.filter((v) => v.language.name === 'en' && v.version.name === 'red')[0].flavor_text

          })
          .catch((e) => {
            console.log(e);
          });
    }
  }
}
</script>

<style>
html {
  background-color: #DD0000;
}
#app {
  display: flex;
}
</style>
