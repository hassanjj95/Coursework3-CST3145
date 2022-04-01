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
    "id": 1001,
    "image": "images/science.jpg",
    "subject": "Science",
    "Location": "London",
    "price": 10, 
    "availableInventory": 10,
    "rating": 3
    },
    {
      "id": 1002,
      "image": "images/english.jpg",
      "subject": "English",
      "Location": "London",
      "price": 5,
      "availableInventory": 7,
      "rating": 5
    },
    {
      "id": 1003,
      "image": "images/art.jpg",
      "subject": "Art",
      "Location": "London",
      "price": 7.50,
      "availableInventory": 30,
      "rating": 2
    },
    {
      "id": 1004,
      "image": "images/ict.jpg",
      "subject": "ICT",
      "Location": "London",
      "description": "Learn from basic to advance iCT skills",
      "price": 8.50,
      "availableInventory": 11,
      "rating": 5
    },
    {
      "id": 1005,
      "image": "images/math.jpg",
      "subject": "Math",
      "Location": "London",
      "price": 4.99,
      "image": "images/math.jpg",
      "availableInventory": 25,
      "rating": 5
  },
    {
      "id": 1006,
      "image": "images/french.jpg",
      "subject": "French",
      "price": 9,
      "Location": "London",
      "availableInventory": 25,
      "rating": 4
  },
    {
      "id": 1007,
      "image": "images/pe.jpg",
      "subject": "Physical Education",
      "price": 4,
      "Location": "London",
      "availableInventory": 9,
      "rating": 5
  },
    {
      "id": 1008,
      "image": "images/geo.jpg",
      "subject": "Geography",
      "Location": "London",
      "price": 3,
      "availableInventory": 11,
      "rating": 3
  },
    {
      "id": 1009,
      "image": "images/history.jpg",
      "title": "History",
      "price": 8,
      "Location": "London",
      "availableInventory": 13,
      "rating": 3
  },
  {
      "id": 1010,
      "image": "images/music.jpg",
      "title": "Music",
      "price": 20,
      "Location": "London",
      "availableInventory": 15,
      "rating": 4
    }
    
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
