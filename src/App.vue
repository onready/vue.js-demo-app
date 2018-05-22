<template>
  <v-app light>
    <app-toolbar></app-toolbar>
    <v-container grid-list-md text-xs-center>
      <card-list></card-list>
    </v-container>
  </v-app>
</template>

<script>
  import Vue from 'vue'
  import Vuetify from 'vuetify'
  import AppToolbar from './components/AppToolbar'
  import CardList from './components/CardList'
  import 'whatwg-fetch'
  import 'vuetify/dist/vuetify.min.css'

  Vue.use(Vuetify)

  export default {
    name: 'app',
    components: {
      AppToolbar,
      CardList
    }
  }
</script>
