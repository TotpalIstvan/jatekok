<template>
<div>
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
    
    <Sor 
    v-for="row in rows"
    :key="row.nev"
    :row="row"
    @torles = "Torles"
    @mentes = "Mentes"
    />
    <label></label>
    </tbody>
  </table>
  <label></label>
      <button @click="Hozzaad">Hozzáadás</button><br>
</template>
</div>
<script>
import Sor from './Sor.vue'
export default {
    props: ['rows'],
    componets: {Sor}
}
</script>