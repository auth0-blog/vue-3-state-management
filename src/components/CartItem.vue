<template>
    <div class="row cart-item-row">
        <div class="col-md-6">
            <Product :product="product" />
        </div>
        <div class="col-md-4">
            <div class="row">
                <div class="col-md-5">
                    <button @click="changeQuantity()" class="btn btn-primary btn-block">+</button>
                </div>
                <div class="col-md-2 text-center">{{itemQuantity}}</div>
                <div class="col-md-5">
                    <button @click="changeQuantity('decrease')" class="btn btn-warning btn-block">-</button>
                </div>
            </div>
            <div class="row cart-remove-button">
                <div class="col-md-12">
                    <button @click="removeItem()" class="btn btn-danger btn-block">Remove Item</button>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import Product from "./Product.vue";
import {computed} from "vue";
import { useStore } from "vuex";
export default {
    name : "CartItem",
    props : ['product'],
    components : {
        Product
    },
    setup(props){

        const store = useStore();

        let cart = computed(function () {
            return store.state.cart
        });

        let itemQuantity = computed(function(){
             let get_product = cart.value.filter((item) => item.id == props.product.id);

             return get_product[0].quantity;
        })

        function changeQuantity(action = 'add'){

            if(action == 'add'){
                props.product.quantity = props.product.quantity + 1;

                store.commit("updateCartItem", props.product);
            }else{

                if(props.product.quantity > 1){
                    props.product.quantity = props.product.quantity - 1;
                    store.commit("updateCartItem", props.product);
                }else{
                    //Remove the item
                    store.commit("removeCartItem", props.product)
                }
            }
        }

        function removeItem(){
            store.commit("removeCartItem", props.product)
        }

        return {
            cart,
            itemQuantity,
            changeQuantity,
            removeItem
        }
    }
    
}
</script>
<style scoped>
.cart-item-row{
    border-bottom: 1px solid #ccc;
    margin-top: 20px;
}
.cart-remove-button{
    margin-top: 10px;
}
</style>