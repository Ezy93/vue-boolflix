<template>
    <div class="d-flex flex-wrap container">
        
        <ul v-for="(element) in series" :key="element.id" class="mx-2 p-2">
            <li>
                <h6 class="bg-warning p-1">serie</h6>
            </li>
            <li>
                <img class="poster" v-if="(element.backdrop_path !== null)" :src="`https://image.tmdb.org/t/p/w342${element.backdrop_path}`" :alt="element.title">
                <p v-else class="bg-primary">poster non disponibile</p>
            </li>
            <li>
                Titolo: {{element.name}}
            </li>
            <li>
                Titolo originale: {{element.original_name}}
            </li>
            <li>
                Lingua: <img class="my-flag" :src="`https://www.unknown.nu/flags/images/${element.original_language}-100`" :alt="`${element.original_language}`">
            </li>
            <li>
                voto: {{newVoteRange(element.vote_average)}}
            </li>
        </ul>
    </div>
</template>

<script>
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
    methods:{
        newVoteRange(star){
            return Math.ceil(star / 2)
        },
    },
}
</script>

<style lang="scss" scoped>
div{
    
    ul{
            border: 2px solid black;
            list-style-type: none;
            width: calc(100% / 5 - 1rem);
            li{
                padding: .2rem;
                img.my-flag{
                    width: 24px;
                    height: 24px;
                    object-fit: contain;
                }
                img.poster{
                    width: 100%;
                }
            }
        }
}
</style>