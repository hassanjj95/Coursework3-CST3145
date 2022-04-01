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
      "title": "Science",
      "description": "Science is a universal subject that spans the branch of knowledge that examines the structure and behavior of the physical and natural world through observation and experiment.",
      "price": 10,
      "image": "images/science.jpg",
      "availableInventory": 10,
      "rating": 3
    },
    {
      "id": 1002,
      "title": "English",
      "description": "Learn how to interpret texts, oral communication and critical approaches",
      "price": 5,
      "image": "images/english.jpg",
      "availableInventory": 7,
      "rating": 5
    },
    {
      "id": 1003,
      "title": "Art",
      "description": "Learn how to draw.",
      "price": 7.50,
      "image": "images/art.jpg",
      "availableInventory": 30,
      "rating": 2
    },
    {
      "id": 1004,
      "title": "ICT",
      "description": "Learn from basic to advance iCT skills",
      "price": 8.50,
      "image": "images/ict.jpg",
      "availableInventory": 11,
      "rating": 5
    },
    {
      "id": 1005,
      "title": "Math",
      "description": "Tou are going to be able to understand the foundations of mathematics, be able to perform basic computations in higher mathematics, be able to read and understand middle-level proofs, be able to write and understand basic proofs and develop and maintain problem-solving skills",
      "price": 4.99,
      "image": "images/math.jpg",
      "availableInventory": 25,
      "rating": 5
  },
    {
      "id": 1006,
      "title": "French",
      "description": "Learn the french langugue in the most effective way",
      "price": 9,
      "image": "images/french.jpg",
      "availableInventory": 25,
      "rating": 4
  },
    {
      "id": 1007,
      "title": "Physical Education",
      "description": "Learn how to stay fit",
      "price": 4,
      "image": "images/pe.jpg",
      "availableInventory": 9,
      "rating": 5
  },
    {
      "id": 1008,
      "title": "Geography",
      "description": "Learn where are other countries",
      "price": 3,
      "image": "images/geo.jpg",
      "availableInventory": 11,
      "rating": 3
  },
    {
      "id": 1009,
      "title": "History",
      "description": "Learn the most from what happend in the past",
      "price": 8,
      "image": "images/history.jpg",
      "availableInventory": 13,
      "rating": 3
  },
  {
      "id": 1010,
      "title": "Music",
      "description": "Learn how to make music",
      "price": 20,
      "image": "images/music.jpg",
      "availableInventory": 15,
      "rating": 4
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
