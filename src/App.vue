<template lang="html">
  <div>
    <h1>Rick and Morty Encyclopedia</h1>
    <div class="main-container">
      <CharacterList :characters='characters'></CharacterList>
    </div>
  </div>

</template>

<script>
import CharacterList from './components/CharacterList.vue'
import {eventBus} from './main.js'

export default {
  name: 'App',
  data(){
    return {
      characters: [],
      selectedCharacter: null
    };
  },
  mounted(){
    fetch('https://rickandmortyapi.com/api/character/')
    .then(res => res.json())
    .then(chars => this.characters = chars.results)

    eventBus.$on('character-selected', (character) => {
      this.selectedCharacter = character;
    })
  },
  components: {
    CharacterList
  }
}
</script>

<style lang="css" scoped>
.main-container {
  display: flex;
  justify-content: space-between;
}
</style>
