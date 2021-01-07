<template>
    <div class="card mx-3 text-center" style="width: 18rem;">
        <img class="card-img-top" :src="product.image" alt="Card image cap">
        <div class="card-body">
            <h5 class="card-title">{{ product.title }}</h5>
            <p class="card-text text-muted display-4">${{ Number(product.price).toFixed(2) }}</p>
            <button @click="$emit('add-to-cart', product)" class="btn btn-primary" :disabled="isInCart">
                {{ isInCart ? 'Added To Cart' : 'Add to Cart'}}
            </button>
        </div>
    </div>
</template>

<script>
    export default {
        name: "Product",
        props: ['product', 'isInCart'],
    }
</script>
