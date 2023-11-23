<template>
  <div class="container mt-4">
    <h1 class="mb-4" style="text-align: center;">Danh mục sản phẩm</h1>
    <div class="row">
      <div class="col-md-3 mb-4" v-for="product in products" :key="product.id">
        <div class="card">
          <img :src="product.image" class="card-img-top image-container" alt="Comic">
          <div class="card-body">
            <h5 style="text-align: center;color: #17a2b8;font-weight: bold;">{{ product.name }}</h5>
            <p class="card-text">{{ product.description }}</p>
            <p class="card-text" style="color: #ff0000;font-weight: 600;">Giá: {{ product.price }}.000 đồng</p>
            <div style="display: flex;">
              <button style="margin: 5px;padding: 5px;" @click="addToCart( product._id, quantity )" class="btn btn-info">Thêm vào giỏ</button>
              <button style="margin: 5px;padding: 5px;" @click="submitForm()" class="btn btn-info">Đặt hàng</button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import webService from '../services/web.service';
import axios from 'axios';
  export default {
    data() {
    return {
      products: [],
      quantity: 1,
    };
  },
  created() {
    this.fetchProducts();
  },
  methods: {
    async fetchProducts() {
      try {
        this.products = await webService.getProduct();
      } catch (error) {
        console.error(error);
      }
    },
    async addToCart(id, quantity) {
      const data = {
        email: this.$store.state.email,
        id: id,
        quantity: quantity,
      };
      axios.post('http://localhost:3004/api/cart', data);
      alert('đã thêm vào giỏ hàng!!');
    }

    
  },
}
  
</script>

<style>
.image-container {
  margin:0px 0 0 0px;
  width: 200px;  /* Định rõ kích thước chiều rộng */
  height: 300px; /* Định rõ kích thước chiều cao */
  object-fit: cover; /* Giữ tỷ lệ khung hình và cắt ảnh để vừa khung */
}

.card{
  width: 250px;
}
</style>