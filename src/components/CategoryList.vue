<template>
    <div>
        <nav class="navbar navbar-light bg-light">
            <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
                <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="navbarSupportedContent">
                <ul class="navbar-nav mr-auto">
                    <li class="nav-item" v-for="cate in category" :key="cate.id">
                        <a class="list-group-item" @click="getCategoryId(cate)">{{cate.categoryName}}</a>
                    </li>
                    <li class="nav-item">
                        <i class="fa fa-snowflake-o"></i>
                    </li>
                    <li class="nav-item">
                        <i class="fa fa-snowflake-o"></i>
                    </li>
                </ul>
            </div>
        </nav>
        <div class="list mt-5">
            <div class="list-group" id="list-tab" role="tablist" v-for="cate in category" :key="cate.id">
                <a class="list-group-item" @click="getCategoryId(cate)">{{cate.categoryName}}</a>
            </div>
        </div>
    </div>
</template>



<script>
export default {
    data(){
        return{
            category:[]
        }
    },
    created(){
        fetch('http://localhost:3000/categories')
        .then((res) => {return res.json()})
        .then((res) => {this.category = res})
    },
    methods:{
        getCategoryId(cate){
            let item = cate.id
            this.$emit('changeCategory', item)
        }
    }
}
</script>



<style scoped>

@media only screen and (min-width: 600px) {
    nav {
        display: none;
    }
}
@media only screen and (max-width: 600px) {
    .list {
        display: none;
    }
}

</style>