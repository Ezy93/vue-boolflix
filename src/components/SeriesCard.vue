<template>
    <div class="d-flex flex-wrap container-fluid">
        
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
                Lingua: <img :src="require(`@/assets/img/${element.original_language}.png`)" :alt="`${element.original_language}`">
            </li>
            <li>
                Voto:{{element.vote_average}}
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

                img.poster{
                    width: 100%;
                }
            }
        }
}
</style>