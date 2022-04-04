<template>
    <div class="d-flex flex-wrap container">
        <div v-for="(element) in films" :key="element.id" class="my-card mx-2 mb-2 position-relative">
            <img class="my-poster h-100 w-100 " v-if="(element.backdrop_path !== null)" :src="`https://image.tmdb.org/t/p/w342${element.poster_path}`" :alt="element.title">
            <p v-else class="bg-dark  text-white text-center">poster non disponibile</p>
            <div class="my-description px-2 my-5 position-relative text-white">
                <div>
                    Titolo: {{element.title}}
                </div>
                <div>
                    Titolo originale: {{element.original_title}}
                </div>
                <div>
                    Lingua: <img class="my-flag" :src="`https://www.unknown.nu/flags/images/${element.original_language}-100`" :alt="`${element.original_language}`">
                </div>
                <div class="d-flex align-items-center">
                    
                    <div v-if="(newVoteRange(element.vote_average) < 0)">
                        {{newVoteRange(element.vote_average)}} 
                    </div>
                    <div v-if="(newVoteRange(element.vote_average) >= 0)">
                        vote:
                    </div>
                    <div class="ms-1">
                        <font-awesome-icon icon="fa-solid fa-star"  :class="{active: (newVoteRange(element.vote_average) > 0)}"/>
                        <font-awesome-icon icon="fa-solid fa-star"  :class="{active: (newVoteRange(element.vote_average) > 1)}"/>
                        <font-awesome-icon icon="fa-solid fa-star"  :class="{active: (newVoteRange(element.vote_average) > 2)}"/>
                        <font-awesome-icon icon="fa-solid fa-star"  :class="{active: (newVoteRange(element.vote_average) > 3)}"/>
                        <font-awesome-icon icon="fa-solid fa-star"  :class="{active: (newVoteRange(element.vote_average) > 4)}"/>
                        
                    </div>
            
                </div>
                <div class="mt-1">
                    {{element.overview}}
                </div>
            </div>
        </div>
        <!-- <ul v-for="(element) in films" :key="element.id" class="mx-2 p-2">
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
            <li class="d-flex align-items-center">
                <div v-if="(newVoteRange(element.vote_average) < 0)">
                    {{newVoteRange(element.vote_average)}} 
                </div>
                <div v-if="(newVoteRange(element.vote_average) >= 0)">
                    vote:
                </div>
                <div class="ms-1">
                    <font-awesome-icon icon="fa-solid fa-star"  :class="{active: (newVoteRange(element.vote_average) > 0)}"/>
                    <font-awesome-icon icon="fa-solid fa-star"  :class="{active: (newVoteRange(element.vote_average) > 1)}"/>
                    <font-awesome-icon icon="fa-solid fa-star"  :class="{active: (newVoteRange(element.vote_average) > 2)}"/>
                    <font-awesome-icon icon="fa-solid fa-star"  :class="{active: (newVoteRange(element.vote_average) > 3)}"/>
                    <font-awesome-icon icon="fa-solid fa-star"  :class="{active: (newVoteRange(element.vote_average) > 4)}"/>
                    
                </div>
            </li>
        </ul> -->
        
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
            counterArray:[0,1,2,3,4]
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
div{
    div.my-card{
        border: 2px solid black;
        list-style-type: none;
        width: calc(100% / 5 - 1rem);
        height: 23rem;

        img.my-poster{
            position: absolute;
            object-fit: cover;
            height: 100%;
        }

        

        div.my-description{
            
            div.mt-1{
                overflow-y: auto;
                height: 10rem;
            }
        }
        
        
        img.my-flag{
            width: 24px;
            height: 24px;
            object-fit: contain;
        }
    }
        .active{
            color: #ffbd00;
        } 
    /* ul{
        border: 2px solid black;
            list-style-type: none;
            width: calc(100% / 5 - 1rem);
            li{
                padding: .2rem;
                img.poster{
                    width: 100%;
                }
            }
        }*/
}
</style>