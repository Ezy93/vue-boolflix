<template>
    <div class="d-flex flex-wrap container">

        <div v-for="(element) in films" :key="element.id" class="my-card mx-2 mb-2 position-relative flex-shrink-0">
            <img class="my-poster h-100 w-100" v-if="(element.poster_path !== null)" :src="`https://image.tmdb.org/t/p/w342${element.poster_path}`" :alt="element.title">
            
            <div class="my-description px-2 py-5 position-relative text-white h-100 bg-black">
                <div>
                    <span class="fw-bold">Titolo:</span> {{element.title}}
                </div>
                <div>
                    <span class="fw-bold">Titolo Originale:</span> {{element.original_title}}
                </div>
                <div>
                    <span class="fw-bold">Lingua:</span> <img class="my-flag" :src="`https://www.unknown.nu/flags/images/${element.original_language}-100`" :alt="`${element.original_language}`">
                </div>
                <div class="d-flex align-items-center">
                    
                    <div v-if="(newVoteRange(element.vote_average) < 0)">
                        {{newVoteRange(element.vote_average)}} 
                    </div>
                    <div v-if="(newVoteRange(element.vote_average) >= 0)">
                        <span class="fw-bold">Vote:</span>
                    </div>
                    <div class="ms-1">
                        <font-awesome-icon icon="fa-solid fa-star" v-for="(star,index) in 5" :key="index"  :class="{active: (newVoteRange(element.vote_average) > index)}"/>
                    </div>
            
                </div>
                <div class="mt-1 pb-2">
                    <span class="fw-bold">Overview:</span> {{element.overview}}
                </div>
            </div>
        </div>
        
    </div>
</template>

<script>
import '../scss/style.scss'
export default {
    name: "MainCard",
    props: {
        'films': Array,
        'series': Array,
    },
    data: function(){
        return{
            
        }
    },
    created: function(){
        
    },
    computed:{
        },
    methods:{
        newVoteRange(star){
            return Math.ceil(star / 2)
        },
        

        
        
    },
}
</script>

<style lang="scss" scoped>

</style>