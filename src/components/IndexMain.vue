<template>
    <main class="d-flex flex-wrap pt-3">
        <ul v-for="(element) in filmsArray" :key="element.id" class="mx-2 p-2">
            <li>
                Titolo: {{element.title}}
            </li>
            <li>
                Titolo originale: {{element.original_title}}
            </li>
            <li><!-- trovare soluzione per prendere le immagini -->
                Lingua: <img :src="require(`@/assets/img/${element.original_language}.png`)" alt="">
            </li>
            <li>
                Voto:{{element.vote_average}}
            </li>
        </ul>
    </main>
</template>

<script>


export default {
    name: "IndexMain",
    props: {
        'filmsArray': Array
    },
    data: function(){
        return{
            filmsList: null,
            seriesList: null,
        }
    },
    created: function(){
        
    },
    methods:{
        
    },
}

</script>

<style lang="scss" scoped>
    ul{
        border: 2px solid black;
        list-style-type: none;
        li{
            padding: .2rem;
        }
    }
</style>