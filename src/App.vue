<template lang="html">
  <div>
    <h1>Rick and Morty Encyclopedia</h1>
    <div class="main-container">

    </div>
  </div>

</template>

<script>
export default {
  name: 'app',
  data(){
    return {
      characters: []
    };
  },
  mounted(){
    fetch('https://rickandmortyapi.com/api/character/')
    .then(res => res.json())
    .then(chars => this.characters = chars.results)
    console.log(this.characters);
  }
}
</script>

<style lang="css" scoped>
</style>
