<template>
 <div id="app" >
  <Tablazat />
</div>
</template>

<script>

import Tablazat from './components/Tablazat.vue'

export default {
  name: 'App',
  components: {
    Tablazat
  },
  data() {
return {
   rows: [
            {
              nev: 'Far Cry 6',
              kiadasi_ev: 2021,
              kiado: 'Ubisoft',
              free_to_play: 'nem'
            },

            {
              nev: 'World of Tanks',
              kiadasi_ev: 2010,
              kiado: 'Wargaming',
              free_to_play: 'igen'
            },

            {
              nev: 'Simcity',
              kiadasi_ev: 2013,
              kiado: 'Electronic Arts',
              free_to_play: 'nem'
              
            }
        ]
      }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
