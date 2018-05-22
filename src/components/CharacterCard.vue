<template>
  <v-card class="character-card elevation-5">
    <v-card-text>{{character.name}}</v-card-text>
  </v-card>
</template>

<script>
  export default {
    name: 'CharacterCard',
    props: ['character']
  }
</script>

<style scoped>

  .character-card {
    margin: 2%;
  }

</style>