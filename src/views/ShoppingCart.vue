<template>
  <div class="home container">
    <div class="row">
      <div class="col-md-8 pt-5">

       <CartItem v-for="product in cart" :product="product" :key="product.id" />
        
      </div>
      <div class="col-md-4 pt-5">
        <!-- <SideNav /> -->
        <Cart />
      </div>
      
    </div>
  </div>
</template>

<script>

import {ref} from "vue";
import CartItem from "../components/CartItem.vue";
import Cart from "../components/Cart.vue";

export default {
  name: 'ShoppingCart',
  components: {
    CartItem,
    Cart
  },

  setup(){

      let cart = ref();

      cart = [
        {
          id : 1,
          name : "Chelsea Shoes",
          price : 200,
          shortdesc : "Best Drip in the Market",
          url : "images/chelsea-shoes.png",
          quantity : 1
        },
        {
          id : 2,
          name : "Kimono",
          price : 50,
          shortdesc : "Classy, Stylish, Dope",
          url : "images/kimono.png",
          quantity : 1
        },
        {
          id : 3,
          name : "Rolex",
          price : 2500,
          shortdesc : "Elegance built in",
          url : "images/rolex.png",
          quantity : 1
        }
       
      ]

      return {
          cart
      }
  }
}
</script>
