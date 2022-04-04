<template>
    <header>
        <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
            <div class="container-fluid">
                <a class="navbar-brand" href="#">
                    <img src="https://upload.wikimedia.org/wikipedia/commons/7/7a/Logonetflix.png" alt="netflix logo">
                </a>
                <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
                    <span class="navbar-toggler-icon"></span>
                </button>
                <div class="collapse navbar-collapse" id="navbarSupportedContent">
                    <ul class="navbar-nav me-auto mb-2 mb-lg-0">
                        <li class="nav-item">
                            <a class="nav-link active" aria-current="page" href="#">Home</a>
                        </li>
                        <li class="nav-item">
                            <a class="nav-link active" href="#">Serie TV</a>
                        </li>
                        <li class="nav-item">
                            <a class="nav-link active" aria-current="page" href="#">Film</a>
                        </li>
                        <li class="nav-item">
                            <a class="nav-link active" href="#">Originali</a>
                        </li>
                        <li class="nav-item">
                            <a class="nav-link active" aria-current="page" href="#">Aggiunti di recente</a>
                        </li>
                        <li class="nav-item">
                            <a class="nav-link active" href="#">La mia lista</a>
                        </li>
                    </ul>
                    <div class="d-flex">
                        <input class="form-control me-2" type="search" placeholder="Search" aria-label="Search" v-model="searchedString" @keyup.enter="stringModifier">
                        <button class="btn " type="submit" @click="stringModifier">Search</button>
                    </div>
                </div>
            </div>
        </nav>

    </header>
</template>

<script>
export default {
    name: "IndexHeader",
    data: function(){
        return{
            searchedString: '',
            queryString: null,
        }
    },
    created: function(){
        
        
        
        
    },
    methods:{
        stringModifier(){
            if(this.searchedString === null || this.searchedString.trim().length === 0){
                this.searchedString = "into the void"
                
            }
            this.queryString =  this.searchedString.trim().split(" ").join("+")
            console.log(this.queryString)
            
            this.$emit('search', this.queryString)
            this.searchedString = ""
        },
        
        
        
    },
}
</script>

<style lang="scss" scoped>
/* stilizzazione di prova da eliminare */
    a.navbar-brand{
        img{
            width: 10rem;
        }
    }
    
    button.btn{
        color: white;
        border: 2px solid white;
    }
</style>