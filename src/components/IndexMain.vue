<template>
    <main class="d-flex flex-wrap flex-column pt-3 bg-dark">
        <FilmsCard
        :films ="filmsArray"
        :series ="seriesArray"
        />
        <SeriesCard
        :films ="filmsArray"
        :series ="seriesArray"
        />
        
        
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
        
    },
}

</script>

<style lang="scss" scoped>
    
</style>