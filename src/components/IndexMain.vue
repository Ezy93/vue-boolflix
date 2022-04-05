<template>
    <main class="d-flex flex-wrap pt-3 bg-dark">
        <FilmsCard
        :films ="filmsArray"
        :series ="seriesArray"
        />
        <SeriesCard
        :films ="filmsArray"
        :series ="seriesArray"
        />
        
        <div class="container">
            <div class="mx-2 text-white">
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
            alerts: "",
        }
    },
    created: function(){
        
    },
    methods:{
        
    },
}

</script>

<style lang="scss" scoped>
    
</style>