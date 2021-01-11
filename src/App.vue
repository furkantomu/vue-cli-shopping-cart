<template>
  <div id="app">
    <div class="container">
      <div class="row">
        <div class="col-md-4">
          
          <category-list @changeCategory=getChangeCategory></category-list>
          
        </div>
        <div class="col-md-8">
          <cart :cart="cart" @getDeleteItemCart=removeFromCart></cart>
          <product-list @setAddtoCart=getAddToCart :product="product"></product-list>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Cart from './components/Cart.vue'
import CategoryList from './components/CategoryList.vue'
import ProductList from './components/ProductList.vue'


export default {
  name: 'App',
  components: {
    CategoryList,
    ProductList,
    Cart
    
  },
  data(){
    return{
      product:[],
      cart:[]
    }
  },
  created(){
    let url ='http://localhost:3000/products'
    fetch(url)
    .then(res => {return res.json()})
    .then(res => {return this.product=res})
  },
    methods:{
    getChangeCategory(item){
      let url ='http://localhost:3000/products'
      if(item){
        url += "?categoryId=" + item
      }
      fetch(url)
      .then(res => {return res.json()})
      .then(res => {return this.product=res})
    },
    getAddToCart(prod){
      let addedItem = this.cart.find(c => c.prod.id === prod.id)
      if(addedItem){
        addedItem.quantity+=1
        addedItem.price += parseInt(prod.unitPrice)
      }
      
      else{
        this.cart.push({prod:prod,quantity:1,price:parseInt(prod.unitPrice)})
      }
    },
    removeFromCart(index){
      // console.log("tıklanılan id:"+ id)
      // for(let i =0; i< this.cart.length;i++){
      //   console.log("cart id:"+this.cart[i].prod.id)
      // }
      this.cart.splice(index,1)
    }
  }
}
</script>

<style>

</style>
