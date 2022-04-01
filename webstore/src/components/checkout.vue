<template>
    <div class="checkOut">
        <h2>Checkout</h2>
        <div v-for='product in cart' :key="product.id" id="shoppingCart">
            <p>
                <img v-bind:src="product.image" width="150" height="150"/>
                <br>
                <b>{{product.subject}}</b>
                <br>
                Location: {{product.location}}
                <br>
                Price: {{product.price}}
                <br>
                Quantity:  x {{product.inCart}}
                <button id="removebutton" @click="removeProduct(product)" >remove</button>
            </p>
            
        </div>
        <div class="checkOut2">
            <p>
                <strong>Name</strong> <input v-model="name"/>
                <strong>Address</strong> <input v-model="address"/>
                <br>
                <br>
                <button id="removebutton">Submit</button>
            </p>
        </div>
    </div>
</template>

<script>
export default {
    name: "CheckOut",
    props: ['cart'],
    data() {
        return {
            name: "",
            address: "",
        };
    },
    methods: {
        removeProduct(product) {
            this.$emit('removeProduct', product)
        }
    }
};
</script>
<style>
.checkOut {
    text-align: left;
    padding: 2%;
    font-size: 20px;
  }
.checkOut2 {
    /* border: 5px solid black; */
    padding: 1%;
    margin: 10px;
    height: 150%;
    background-color: grey;
    text-align: center;
}
input {
      border-radius: 14px;
      font-size: 18px;
  }
#removebutton {
    border-radius: 14px;
    font-size: 100%;
  }
#shoppingCart {
    border: 5px solid black;
    margin: 15px;
    text-align: center;
    width: 30%;
    display: inline-block;
}
</style>