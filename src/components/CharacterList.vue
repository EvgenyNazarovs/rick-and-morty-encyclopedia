<template lang="html">
  <div>
    <ul>
      <CharacterListItem v-for="(character, index) in characters" :character="character" :key="index"></CharacterListItem>
    </ul>

  </div>

</template>

<script>
import CharacterListItem from './CharacterListItem.vue';

export default {
  name: 'CharacterList',
  props: ['characters'],
  components: {
    CharacterListItem
  }
}
</script>

<style lang="css" scoped>
</style>
