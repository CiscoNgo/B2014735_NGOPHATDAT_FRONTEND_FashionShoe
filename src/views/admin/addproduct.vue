<template>
    <div>
      <h2 style="color: #000;text-align:center" >Thêm Sản Phẩm</h2>
      <form @submit.prevent="addProduct" style="max-width: 400px; margin: auto;">
        <div class="mb-3">
          <label for="image" class="form-label" style="color: #336699;">Link Hình Ảnh:</label>
          <input type="text" class="form-control" id="image" v-model="productData.image" required>
        </div>
        <div class="mb-3">
          <label for="productName" class="form-label" style="color: #336699;">Tên Sản Phẩm:</label>
          <input type="text" class="form-control" id="productName" v-model="productData.name" required>
        </div>
        <div class="mb-3">
          <label for="description" class="form-label" style="color: #336699;">Mô tả:</label>
          <input type="text" class="form-control" id="description" v-model="productData.description" required>
        </div>
        <div class="mb-3">
          <label for="productPrice" class="form-label" style="color: #336699;">Giá Sản Phẩm:</label>
          <input type="number" class="form-control" id="productPrice" v-model="productData.price" required>
        </div>
        <button type="submit" class="btn btn-success" >Thêm Sản Phẩm</button>
      </form>
    </div>
  </template>


<script>
import axios from 'axios';

export default {
  data() {
    return {
      productData: {
        image: '',
        name: '',
        description: '',
        price: null,
      }
    };
  },
  methods: {
    addProduct() {
      axios.post('http://localhost:3004/api/addproduct', this.productData);
        alert('Thêm sản phẩm mới thành công!!')
    }
  }
};
</script>