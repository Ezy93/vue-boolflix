<template>
    <header>
        <div class="row">
            <div class="col-12">
                <input type="text" v-model="searchedString">
                
                <div class="btn btn-primary" @click="stringModifier">
                    cerca
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
            searchedString: null,
            queryString: null,
        }
    },
    created: function(){
        
        
        
        
    },
    methods:{
        stringModifier(){
            console.log(this.searchedString.split(" "))
            this.queryString =  this.searchedString.split(" ").join("+")
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