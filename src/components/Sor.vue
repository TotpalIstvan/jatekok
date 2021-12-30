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
        <td v-if="szerkeszt"><input type="text" v-model="ujSor.free_to_play"></td>
        <td v-if="szerkeszt"><button @click="Nyomas">{{ gomb }}</button></td>

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
             Nyomas() {
                if(this.row == null) {
                    this.$emit('hozzaad', {...this.ujSor})
                }   else{
                    this.$emit('mentes', {
                        regi: {...this.row},
                        old: {...this.ujSor}
                    })
                    this.editing = false
                }
                
            }, 
            Szerkesztes() {
                    this.editing = true
                },
            Torles() {
                this.$emit('torles', this.row.nev)
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