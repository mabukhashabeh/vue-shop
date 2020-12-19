<template>
    <div class="container">
        <div class="row">
            <div class="col-7 my-3">
                <div class="row">
                    <div :key="product.id" class="col-6" v-for="product in products">
                        <product @add-to-cart="addToCart(product)" :product="product"
                                 :isInCart="isInCart(product)"></product>
                    </div>
                </div>
            </div>
            <div class="col-5 my-3">
                    <cart @remove-from-cart="removeFromCart($event)" @pay="pay()" :items="cart"></cart>
            </div>
        </div>
    </div>
</template>

<script>

    import products from '@/products.json'
    import Product from '@/components/Product';
    import Cart from "@/components/Cart";

    export default {
        name: 'app',
        components: {
            Product,
            Cart
        },
        data() {
            return {
                products,
                cart: []
            }
        },
        methods: {
            addToCart(product) {
                this.cart.push(product)
            },
            isInCart(product) {

                return this.cart.some(item => item.id === product.id)

            },
            removeFromCart(product){
                this.cart = this.cart.filter(item=> item.id !== product.id)
            },
            pay(){
                alert('Your shopping is completed.')
                this.cart = []
            }
        },

    }

</script>

