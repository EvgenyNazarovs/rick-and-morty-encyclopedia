<template lang="html">
  <div>
    <li v-on:click="handleClick">{{ character.name }}</li>
  </div>

</template>

<script>

import {eventBus} from '../main.js'

export default {
  name: 'CharacterListItem',
  props: ['character'],
  methods: {
    handleClick(){
      eventBus.$emit('character-selected', this.character)
    }
  }
}
</script>

<style lang="css" scoped>
</style>
