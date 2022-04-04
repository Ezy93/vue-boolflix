<template>
    <header>
        <div class="row">
            <div class="col-12 d-flex">
                <div>
                    <input type="text" v-model="searchedString" @keyup.enter="stringModifier">
                </div>
                
                <div>
                    <div class="btn btn-primary" @click="stringModifier">
                        cerca
                    </div>
                </div>
            </div>
        </div>
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
    div.prova{
        height: 100px;
        width: 200px;
    }
</style>