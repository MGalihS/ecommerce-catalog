<template>
  <div class="product-card">
    <div class="product-image">
      <img :src="product.image" :alt="product.title" />
    </div>
    <div class="product-details">
      <h2 class="product-title">{{ product.title }}</h2>
      <p class="product-description">{{ product.description }}</p>
      <p class="product-price">{{ formattedPrice }}</p>
      <button class="buy-button">Buy Now</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ProductCard',
  props: {
    productId: {
      type: Number,
      required: true
    }
  },
  data() {
    return {
      product: {}
    }
  },
  async created() {
    const response = await fetch(`https://fakestoreapi.com/products/${this.productId}`)
    this.product = await response.json()
  },
  computed: {
    formattedPrice() {
      return `$${(this.product.price / 100).toFixed(2)}`
    }
  }
}
</script>

<style scoped>
.product-image {
  flex: 1;
  max-width: 200px;
}

.product-image img {
  width: 100%;
  height: auto;
}
.product-card {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin: 20px;
  padding: 20px;
  background-color: #fff;
  border-radius: 5px;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.3);
}

.product-image {
  flex: 1;
  max-width: 200px;
}

.product-image img {
  width: 100%;
  height: auto;
}

.product-details {
  flex: 2;
  margin-left: 20px;
}

.product-title {
  font-size: 24px;
  font-weight: bold;
  margin: 0 0 10px;
}

.product-description {
  font-size: 16px;
  margin: 0 0 10px;
}

.product-price {
  font-size: 18px;
  font-weight: bold;
  margin: 0 0 10px;
}

.buy-button {
  background-color: #3f51b5;
  color: #fff;
  border: none;
  border-radius: 5px;
  padding: 10px 20px;
  font-size: 16px;
  cursor: pointer;
}
.pagination-btn {
  background-color: #3f51b5;
  color: #fff;
  border: none;
  border-radius: 5px;
  padding: 10px 20px;
  font-size: 16px;
  cursor: pointer;
}

.pagination-btn:hover {
  background-color: #1a237e;
}

.buy-button:hover {
  background-color: #1a237e;
}

</style>
