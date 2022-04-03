<template>
    <div class="d-flex flex-wrap container-fluid">
        <ul v-for="(element) in films" :key="element.id" class="mx-2 p-2">
            <li>
                <h6 class="bg-danger p-1">film</h6>
            </li>
            <li>
                <img class="poster" v-if="(element.backdrop_path !== null)" :src="`https://image.tmdb.org/t/p/w342${element.backdrop_path}`" :alt="element.title">
                <p v-else class="bg-primary">poster non disponibile</p>
            </li>
            <li>
                Titolo: {{element.title}}
            </li>
            <li>
                Titolo originale: {{element.original_title}}
            </li>
            <li>
                Lingua: <img class="my-flag" :src="`https://www.unknown.nu/flags/images/${element.original_language}-100`" :alt="`${element.original_language}`">
            </li>
            <li >
                {{element.vote_average}}
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
    computed:{
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