<template>
    <div>
        <ul class="list-group">
            <li :key="item.id" class="list-group-item" v-for="item in items">
                {{ item.title }}  - ${{ item.price }}
                <button @click="$emit('remove-from-cart', item)" class="btn badge badge-danger float-right">Remove From Cart</button>
            </li>
            <li class="list-group-item">
                <h4 class="text-center">$ {{ total.toFixed(2) }}</h4>
            </li>
        </ul>
        <button @click="$emit('pay')" class="btn btn-info btn-block my-3" :disabled="isEmptyCart">Pay</button>
    </div>

</template>

<script>
    export default {
        name: "Cart",
        props: ['items'],
        computed: {
            total(){
                return this.items.reduce((acc, item) => acc + Number(item.price), 0)
            },
            isEmptyCart(){
                return this.items.length === 0
            }
        }
    }
</script>
