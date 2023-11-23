<template>
    <div>
      <h2 style="color: #000;">Chỉnh Sửa Sản Phẩm</h2>
      <form @submit.prevent="editProduct">
        <div class="form-group">
          <label for="image" >Link Hình Ảnh:</label>
          <input type="text" class="form-control" id="image" v-model="productData.image" required>
        </div>
        <div class="form-group">
          <label for="productName" >Tên Sản Phẩm:</label>
          <input type="text" class="form-control" id="productName" v-model="productData.name" required>
        </div>
        <div class="form-group">
          <label for="description" >Mô tả:</label>
          <input type="text" class="form-control" id="description" v-model="productData.description" required>
        </div>
        <div class="form-group">
          <label for="productPrice" >Giá Sản Phẩm:</label>
          <input type="number" class="form-control" id="productPrice" v-model="productData.price" required>
        </div>
        <button type="submit" class="btn btn-warning" >Cập Nhật Sản Phẩm</button>
      </form>
    </div>
  </template>
  
  <script>
  import webService from '../../services/web.service';
  import axios from 'axios';

  export default {
    data() {
      return {
        productData: {
          image: '',
          name: '',
          description: '',
          price: null,
        },
      };
    },
    created() {
        this.fetchProduct();
    },
    
    methods: {
        async fetchProduct() {
            this.productData = await webService.getProductId(this.$route.params.id);
        },
        async editProduct() {
            axios.put(`http://localhost:3004/api/editproduct?id=${this.$route.params.id}`, this.productData);
            const confirmEdit = confirm("Cập nhật thành công. Bạn có muốn quay lại trang sản phẩm không??");
            if(confirmEdit) {
                window.history.back();
            }
        }
    }
  };
  </script>
  