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
    @szerkeszt = "Szerkeszt"
    />
    <label></label>
    </tbody>
  </table>
  <label class="frpLbl"> Free-to play </label><br>
      <button @click="Hozzaad">Hozzáadás</button><br>
      </div>
</template>

<script>
import Sor from './Sor.vue'
export default {
  
  name: 'App',
  components: {
    Sor
    
  },
  data() {
      return {
        szerkesztett: {
          old: {
            nev: '',
            kiadasi_ev: null,
            kiado: '',
            free_to_play: ''
          },
          new: {
            nev: '',
            kiadasi_ev: null,
            kiado: '',
            free_to_play: ''
          }
        },
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
      
  },
  methods: {
        Torles(nev) {
            this.rows = this.rows.filter(function (item) {
              return item.nev != nev
            })
        }, 
        Szerkeszt(szerkesztett) {
            this.szerkesztett.old = {...szerkesztett}
            this.szerkesztett.new = {...szerkesztett}
        }, 
        Mentes(szerkesztett) {
            this.rows = this.rows.map(function (item) {
              if (item.nev != szerkesztett.old.nev) {
                return item;
              }
              return {...szerkesztett.new}
            })
            this.szerkesztett.old.nev = ''
        },
        Hozzaad(row) {
          var letezik = false
          this.rows.forEach(function(item) {
            if (item.nev == row.nev) {
              letezik = true
            }
          })
          if (!letezik) {
            this.rows.push({...row})
          } 
         
         
          else{
            this.rows = this.rows.map(function (item) {
              if(item.nev != row.nev) {
                return item
              }
              return row
            })
          }
        }
   },
  computed: {
      
  } 
}

</script>

<style>
.frpLbl {
  float: left;
}
</style>