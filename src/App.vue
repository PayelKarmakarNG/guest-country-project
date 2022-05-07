<template>
  <div id="app">
    <v-app>
      <v-container fluid pa-0> 
        <GuestCountryCard/>
      </v-container>
    </v-app>
  </div>
</template>

<script>
import GuestCountryCard from './components/GuestCountryCard.vue'

export default {
  name: 'App',
  components: {
    GuestCountryCard
  }
}
</script>

<style>
  #app {
    background: #E5E5E5;
    /* font-family: 'Inter'; */
    font-style: normal;
    font-weight: 400;
    font-size: 12px;
    line-height: 20px;
  }
</style>
