<template>
    <div class="col mb-4">
        <div class="card">
            <img :src="product.url" class="card-img-top" alt="...">
            <div class="card-body">
            <h5 class="card-title">{{product.name}}</h5>
            <p class="card-text">
                ${{product.price}}
                <br/>
                <small>
                {{product.shortdesc}}
                </small>
            </p>
            <button @click="addToCart()" class="btn btn-primary btn-block" :disabled="itemAlreadyInCart">{{itemAlreadyInCart? "Added" : "Add to Cart"}}</button>
            </div>
        </div>
    </div>
</template>

<script>
import {computed} from "vue";
import {useStore} from "vuex";

export default {
    name : "Product",
    props : ['product'],

    setup(props){

        const store = useStore();

        let cart = computed(function () {
            return store.state.cart
        });

        let itemAlreadyInCart = computed(function() {
            let inCart = false;

            cart.value.forEach(item => {
                if(item.id == props.product.id){
                    inCart = true;
                }
            });

            return inCart;
        });

        function addToCart(){
            if(!itemAlreadyInCart.value){
                store.commit("addCartItem", props.product);
            }else{
                alert("Item already added to Cart");
            }
        }

        return {
            cart, 
            itemAlreadyInCart,
            addToCart
        }
    }
}
</script>