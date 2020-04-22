<template lang="html">
  <div>
    <h1>Rick and Morty Encyclopedia</h1>
    <div class="main-container">
      <label for="character-select">Select a Character</label>
      <select id="character-select" v-model="selectedCharacter">
        <option disabled value="">Select a character</option>
        <option v-for="character in characters" :value="character">{{character.name}}</option>
      </select>
      
      <CharacterItemDetail v-if="selectedCharacter" :character="selectedCharacter"></CharacterItemDetail>
    </div>
  </div>

</template>

<script>
import CharacterList from './components/CharacterList.vue'
import {eventBus} from './main.js'
import CharacterItemDetail from './components/CharacterItemDetail.vue'

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
      console.log('character:', this.selectedCharacter);
    })
  },
  components: {
    CharacterList,
    CharacterItemDetail
  }
}
</script>

<style lang="css" scoped>
.main-container {
  display: flex;
  justify-content: space-between;
}
</style>
