<template>
  <div class="card-list">
    <v-progress-circular v-if="loading" size="50" indeterminate color="primary"></v-progress-circular>
    <v-layout v-else row wrap>
      <v-flex xs3 offset-xs9>
        <v-text-field prepend-icon="search" placeholder="Search by name" @input="filterByName"></v-text-field>
      </v-flex>
      <v-flex v-for="(character, i) in filteredCharacters" :key="i" xs4>
        <character-card :character="character"></character-card>
      </v-flex>
    </v-layout>
  </div>
</template>

<script>
  import CharacterCard from './CharacterCard'

  export default {
    name: 'CardList',
    components: {CharacterCard},
    data: () => {
      return {
        characters: [],
        filteredCharacters: [],
        loading: true
      }
    },
    mounted: async function () {
      const characters = await getCharacters()
      this.loading = false
      this.characters = characters
      this.filteredCharacters = characters
    },
    methods: {
      filterByName: function (name) {
        this.filteredCharacters = this.characters.filter(character =>
          character.name.toLowerCase().includes(name))
      }
    }
  }

  const getCharacters = async () => {
    const response = await fetch('https://swapi.co/api/people/')
    const jsonResponse = await response.json()
    return jsonResponse.results
  }
</script>

<style scoped>

  .card-list {
    text-align: center;
  }

</style>