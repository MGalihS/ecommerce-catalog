<template>
  <div class="app">
    <h1>Ecommerce App</h1>
    <div class="product-container">
      <product-card :product-id="productId[0]" v-if="currentProduct === 1" />
      <product-card :product-id="productId[1]" v-if="currentProduct === 2" />
      <div class="product-card" v-if="currentProduct === 3">
        <h2>This product is unavailable to show</h2>
      </div>
    </div>
    <div class="button-container">
      <button @click="previousProduct">Previous Product</button>
      <button @click="nextProduct">Next Product</button>
    </div>
  </div>
</template>

<script>
import ProductCard from './components/ProductCard.vue'

export default {
  name: 'App',
  components: {
    ProductCard
  },
  data() {
    return {
      productId: [3, 4, 5],
      currentProduct: 1
    }
  },
  methods: {
    previousProduct() {
      if (this.currentProduct > 1) {
        this.currentProduct--
      }
    },
    nextProduct() {
      if (this.currentProduct < 3) {
        this.currentProduct++
      }
    }
  }
}
</script>

<style>
h1 {
  color: white;
}
h2 {
  color: white;
}
.app {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100vh;
}

.product-container {
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 20px;
}

.button-container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 200px;
}

/* Gambar di sebelah kiri, teks di sebelah kanan */
.product-card {
  display: flex;
  align-items: center;
  width: 100%;
  max-width: 800px;
  margin: 20px auto;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 5px;
}

.product-image {
  margin-right: 20px;
  flex: 0 0 auto;
}

.product-image img {
  max-width: 100%;
  height: auto;
}

.product-details {
  flex: 1 1 auto;
}

.product-title {
  font-size: 24px;
  margin: 0;
}

.product-description {
  font-size: 16px;
  margin: 10px 0;
}

.product-price {
  font-size: 24px;
  font-weight: bold;
  margin-bottom: 20px;
}

.buy-button {
  background-color: #007aff;
  color: #fff;
  border: none;
  border-radius: 5px;
  padding: 10px;
  font-size: 16px;
  cursor: pointer;
  align-self: flex-start;
}

.buy-button:hover {
  background-color: #0066d9;
}

/* style for button Next Product and Previous Product */
.button-container {
  display: flex;
  justify-content: space-between;
  margin-top: 1rem;
}

.button-container button {
  border: none;
  padding: 0.8rem 1.2rem;
  border-radius: 0.3rem;
  color: white;
  background-color: #4a4e69;
  cursor: pointer;
  transition: all 0.3s ease-in-out;
}

.button-container button:hover {
  background-color: #3f3f3f;
}

.button-container button:focus {
  outline: none;
}

body {
  background-image: linear-gradient(to bottom, #3f3f3f 60%, #f2f2f2 40%);
  background-size: cover;
}

</style>
