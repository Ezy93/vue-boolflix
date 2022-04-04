<template>
    <main class="d-flex flex-wrap pt-3">
        <FilmsCard
        :films ="filmsArray"
        :series ="seriesArray"
        />
        <SeriesCard
        :films ="filmsArray"
        :series ="seriesArray"
        />
        
        <div class="container">
            <div class="mx-2">
                {{zeroResults()}}
            </div>
        </div>
    </main>
</template>

<script>
import FilmsCard from "./FilmsCard.vue"
import SeriesCard from "./SeriesCard.vue"

export default {
    name: "IndexMain",
    components:{
        FilmsCard,
        SeriesCard
    },
    props: {
        'filmsArray': Array,
        'seriesArray': Array,
    },
    data: function(){
        return{
            
        }
    },
    created: function(){
        
    },
    methods:{
        zeroResults(){
            if(this.seriesArray.length === 0 && this.filmsArray.length === 0 ){
                return "la tua ricerca non ha prodotto risultati ne tra le serie tv ne tra i films"
            }else if(this.filmsArray.length === 0){
                return "la tua ricerca non ha prodotto risultati tra i films"
            }else if(this.seriesArray.length === 0){
                return "la tua ricerca non ha prodotto risultati tra le serie tv"
            }
        }
    },
}

</script>

<style lang="scss" scoped>

</style>