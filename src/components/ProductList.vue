<template>
    <div class="prod mt-5">
        <div class="row"  v-for="prod in product" :key="prod.id">
            <div class="col-md-12">
                <div class="card">
                    <div class="card-body">
                        <h5 class="card-title">{{prod.productName}}</h5>
                        <p class="card-text">{{prod.quantityPerUnit}}-${{prod.unitPrice}}</p>
                        <a class="btn btn-primary" @click="addToCart(prod)">Add to Cart</a>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>



<script>
export default {
    props:['product'],
    methods:{
        addToCart(prod){
            this.$emit('setAddtoCart', prod)
        }
    }
}
</script>




<style >
    a{
        color: white;
    }
</style>

