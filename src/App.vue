<template>
  
  <table border="1">
    <thead>
      <tr>
      <th>Név</th>
      <th>Kiadási év</th>
      <th>Kiadó</th>
      <th>Free-to-play?</th>
      </tr>
    </thead>
    <tbody>
    <tr>
      <td>Far Cry 6</td>
      <td>2021</td>
      <td>Ubisoft</td>
      <td>nem</td>
    </tr>
    <tr>
      <td>World of Tanks</td>
      <td>2010</td>
      <td>Wargaming</td>
      <td>igen</td>
    </tr>
    <tr>
      <td>Simcity</td>
      <td>2013</td>
      <td>Electronic Arts</td>
      <td>nem</td>
    </tr>
    </tbody>
  </table>
</template>

<script>


export default {
  name: 'App',
  components: {
    
  },
  data() {
      return {
        rows: [
            {
              nev: 'Far Cry 6',
              kiadasi_ev: 2021,
              kiado: 'Ubisoft',
              free_to_play: false
            },

            {
              nev: 'World of Tanks',
              kiadasi_ev: 2010,
              kiado: 'Wargaming',
              free_to_play: true
            },

            {
              nev: 'Simcity',
              kiadasi_ev: 2013,
              kiado: 'Electronic Arts',
              free_to_play: false
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
