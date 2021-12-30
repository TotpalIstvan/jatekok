<template>
    <tr>
        <td>{{ row.nev }}</td>
        <td>{{ row.kiadasi_ev }}</td>
        <td>{{ row.kiado }}</td>
        <td>{{ row.free_to_play }}</td>
        <td><button @click="Torles()">Törlés</button></td>
        <td><button @click="Szerkesztes()">Szerkesztés</button></td>
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
        }
    }
}
</script>