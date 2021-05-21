<template>
  <div class="home container">
    <div class="row">
      <div class="col-md-9 pt-5">

       <div class="row row-cols-1 row-cols-sm-2 row-cols-md-3 row-cols-lg-3 row-cols-xl-3">
          <Product v-for="product in products" :product="product" :key="product.id" />
       </div>
        
      </div>
      <div class="col-md-3 pt-5">
        <!-- <SideNav /> -->
        <Cart />
      </div>
      
    </div>
  </div>
</template>

<script>

import Product from "../components/Product.vue";
import Cart from "../components/Cart.vue";

import { ref } from "vue";

export default {
  name: 'Home',
  components: {
    Product,
    Cart
  },
  setup(){

    let products = ref();

    products = [
        {
          id : 1,
          name : "Chelsea Shoes",
          price : 200,
          shortdesc : "Best Drip in the Market",
          url : "images/chelsea-shoes.png"
        },
        {
          id : 2,
          name : "Kimono",
          price : 50,
          shortdesc : "Classy, Stylish, Dope",
          url : "images/kimono.png"
        },
        {
          id : 3,
          name : "Watch",
          price : 2500,
          shortdesc : "Elegance built in",
          url : "images/rolex.png"
        },
        {
          id : 4,
          name : "Wallet",
          price : 80,
          shortdesc : "Sleek, Trendy, Clean",
          url : "images/wallet.png"
        },
        {
          id : 5,
          name : "Lady Handbags",
          price : 230,
          shortdesc : "Fabulous, Exotic, Classy",
          url : "images/handbag.png"
        },
        {
          id : 6,
          name : "Casual Shirts",
          price : 30,
          shortdesc : "Neat, Sleek, Smart",
          url : "images/shirt.png"
        }
    ]

    return {
      products
    }
  },
  
}
</script>
