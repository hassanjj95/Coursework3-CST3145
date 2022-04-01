<template>
  <div id="app">
    <header>
        <h1>{{sitename}}</h1>

      <!-- CHECKOUT BUTTON -->
      <div class="checkOutBut">
        <button @click='showCheckout'>
          {{this.cart.length}} Checkout
        </button>
      </div>
        
    </header>
    <div v-if='showProduct'>
      <product-list :products='products' @addProduct='addToCart'></product-list>
    </div>
    <div v-else>
      <checkout :cart='cart' @removeProduct='removeFromCart'></checkout>
    </div>
  </div>
</template>

<script>
import productList from './components/productlist.vue'
import checkout from './components/checkout.vue'

export default {
  name: 'App',
  components: {
    productList,
    checkout
  },
  data() {
    return {
      sitename: "After School Club",
      cart: [],
      showProduct: true,
      products: [
       
    { 
           id: 1,
          image: "science.png",
          subject: "Science",
          location: "London",
          price: 10,
          availableInventory: 5,
          rating: 5,
          inCart: 0
    },
    {
      id: 2,
          image: "english.jpg",
          subject: "English",
          location: "Malta",
          price: 120,
          availableInventory: 5,
          rating: 2,
          inCart: 0
    },
    {
          id: 3,
          image: "art.png",
          subject: "Science",
          location: "London",
          price: 77,
          availableInventory: 5,
          rating: 4,
          inCart: 0
    },
    {
      
    },
    {
          id: 4,
          image: "ict.jpg",
          subject: "ICT",
          location: "London",
          price: 83,
          availableInventory: 5,
          rating: 2,
          inCart: 0
  },
    {
      id: 5,
          image: "geo.jpg",
          subject: "Geography",
          location: "Malta",
          price: 33,
          availableInventory: 5,
          rating: 3,
          inCart: 0
  },
    {
       id: 6,
          image: "pe.jpg",
          subject: "Phisical Education",
          location: "London",
          price: 16,
          availableInventory: 5,
          rating: 4,
          inCart: 0
  },
    {
          id: 7,
          image: "history.jpg",
          subject: "History",
          location: "Malta",
          price: 83,
          availableInventory: 5,
          rating: 2,
          inCart: 0
  },
    {
          id: 8,
          image: "french.jpg",
          subject: "French",
          location: "London",
          price: 33,
          availableInventory: 5,
          rating: 3,
          inCart: 0
  },
  {
       id: 9,
          image: "music.jpg",
          subject: "Music",
          location: "London",
          price: 33,
          availableInventory: 5,
          rating: 3,
          inCart: 0
    },
      ],
    };
  },
  methods: {
    showCheckout: function(){
      this.showProduct = this.showProduct ? false : true;
      },
      addToCart(product) {
        let added = false;
        this.cart.forEach((product2) => {
          if (product2.id === product.id) {
            product.inCart++;
            added = true;
          }
        });
        if (!added) {
        this.cart.push(product)
        product.inCart = 1;
        }
        product.availableInventory --
      },
      removeFromCart(product) {
        this.cart.forEach(product2 => {
          if (product2.id === product.id) {
            product.availableInventory ++;
            product.inCart --;
            if (product.inCart == 0) {
            this.cart.splice(this.cart.indexOf(product), 1)
            }
          }
      });
    },
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
#productLists {
    box-sizing: border-box;
  }
</style>
