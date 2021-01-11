<template>
    <div class="cart mt-1">
        <!-- Button trigger modal -->
        <button type="button" class="btn btn-primary" data-toggle="modal" data-target="#exampleModalLong">
        Shopping Cart <span class="badge badge-light">{{cart.length}}</span> 
        </button>
            <!-- Modal -->
        <div class="modal fade" id="exampleModalLong" tabindex="-1" role="dialog" aria-labelledby="exampleModalLongTitle" aria-hidden="true">
            <div class="modal-dialog" role="document">
                <div class="modal-content">
                    <div class="modal-header">
                        <h5 class="modal-title" id="exampleModalLongTitle">Shopping Cart {{cart.length}} items</h5>
                        <button type="button" class="close" data-dismiss="modal" aria-label="Close">
                        <span aria-hidden="true">&times;</span>
                        </button>
                    </div>
                    <div class="modal-body d-flex justify-content-between" v-for="(item,index) in cart" :key="index" >
                        <div>
                            <span class="badge badge-secondary mr-2">{{item.quantity}}</span>
                            <span class="h5">{{item.prod.productName}}</span>
                            <span class="blockquote-footer ml-4">${{item.price}}</span>
                            
                        </div>    
                        <span><button class="btn btn-danger" @click="setDeletefromCart(index)"> Delete </button></span>
                    </div>    
                        






                    <div class="modal-footer">
                        <p >Cart Total: ${{getTotal}}</p>
                        <button type="button" class="btn btn-secondary" data-dismiss="modal">Close</button>
                        
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>



<script>
export default {
    props:['cart'],
    data(){
        return{   
        }
    },
    computed:{
        getTotal(){
            let total = 0;
            let sonuc = 0;
            this.cart.forEach(e => {
                total += parseInt(e.price)
            })
        return sonuc += total;
        },
    },
    methods:{
        setDeletefromCart(index){
            // let id = item.prod.id;
            this.$emit('getDeleteItemCart',index)
            
        },
        
    }
}
</script>



<style >
    .cart{
        position: absolute;
        right: 20px;
        top: 0px;
    }
    @media only screen and (max-width: 600px) {
    .cart {
        top:-50px
    }

    

}
</style>