<template>

    <main>
        <div>
            <div v-for="product in products" :key="product.id"  class="productLists">
                <figure>
                    <img v-bind:src="product.image" width="200" height="200"/>
                </figure>
                <h2>{{product.subject}}</h2>
                <p>Location: {{product.location}}</p>
                <p>Price: {{product.price}}</p>
                <p>Available stock: {{product.availableInventory}}</p>
                <p>Rating: {{product.rating}}</p>
                <button @click="addToCart(product)">Add to cart</button>
                <br>
            </div>
            <br>
        </div>
    </main>
</template>

<script>

 export default {
     name: "ProductList",
     props: ['products'],
     data() {
         return {}
     },
     methods: {
         addToCart(product) {
            this.$emit('addProduct', product);
         },

     },
 };

</script>

<style>
.productLists {
    border: 5px solid black;
    float: left;
    width: 30%;
    padding: 10px;
    margin: 15px;
}

</style>