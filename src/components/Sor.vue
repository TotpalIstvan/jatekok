<template>

    <tr>
        <td v-if="!szerkeszt">{{ row.nev }}</td>
        <td v-if="!szerkeszt">{{ row.kiadasi_ev }}</td>
        <td v-if="!szerkeszt">{{ row.kiado }}</td>
        <td v-if="!szerkeszt">{{ row.free_to_play }}</td>
        <td v-if="!szerkeszt">
        <button @click="Torles">Törlés</button>
        <button @click="Szerkesztes">Szerkesztés</button>
        </td>
        <td v-if="szerkeszt"><input type="text" v-model="ujSor.nev"></td>
        <td v-if="szerkeszt"><input type="number" v-model="ujSor.kiadasi_ev"></td>
        <td v-if="szerkeszt"><input type="text" v-model="ujSor.kiado"></td>
        <td v-if="szerkeszt "><input type="text" v-model="ujSor.free_to_play"></td>
        <td v-if="szerkeszt"><button>{{ gomb }}</button></td>
        
        <td v-if="Hozzaad"><input type="text" v-model="nev"></td>
        <td v-if="Hozzaad"><input type="number" v-model="kiadasi_ev"></td>
        <td v-if="Hozzaad"><input type="text" v-model="kiado"></td>
        <td v-if="Hozzaad"><input type="text" v-model="free_to_play"></td>
    </tr>
    

</template>

<script>
export default {
    props: ['row'], 
    data() {
            return{
                editing: false,
                ujSor: {
                    nev: this.row == null ? '' : this.row.nev,
                    kiadasi_ev: this.row == null ? '' : this.row.kiadasi_ev,
                    kiado: this.row == null ? '' : this.row.kiado,
                    free_to_play: this.row == null ? '' : this.row.free_to_play
                }
            }
    },
    methods: {
             
            Szerkesztes() {
                    this.editing = true
                },
            Torles() {
                this.$emit('torles', this.row.nev)
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
        szerkeszt() {
            return this.row == null || this.editing
        },
        gomb() {
            return this.row == null ? 'Szerkesztés' : 'Mentés'
        }
    }
}
</script>