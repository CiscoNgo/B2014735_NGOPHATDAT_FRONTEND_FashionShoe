<template>
    <div class="container" v-if="orderedProducts && orderedProducts.length">
      <h1 style="text-align: center;" class="mb-4">Đơn đặt hàng của bạn</h1>
      <table class="table">
      <thead>
        <tr>
          <th scope="col">Sản phẩm</th>
          <th scope="col">Tên sản phẩm</th>
          <th scope="col">Đơn giá</th>
          <th scope="col">Số lượng</th>
          <th scope="col">Tổng tiền</th>
          <th scope="col">Trạng thái</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="product in orderedProducts[0].listProduct" :key="product._id">
          <td>
            <img :src="product.product.image" class="card-img-top image-container" style="height: 100px;" alt="Comic">
            </td>
          <td>{{ product.product.name }}</td>
          <td>{{ product.product.price }}.000 đồng</td>
          <td>{{ product.quantity }}</td>
          <td>{{ product.product.price * product.quantity}}.000 đồng</td>
          <td>
            {{ orderedProducts[0].status }}
          </td>
        </tr>
      </tbody>
    </table>
    </div>
    <div v-else>
      <p>Không có dữ liệu giỏ hàng.</p>
    </div>
  </template>

<script>
import webService from '../services/web.service';
export default {
    data() {
        return {
        orderedProducts: [], 
        };
    },
    created() {
        this.fetchCart();
    },
    methods: {
        async fetchCart() {
            try {
                this.orderedProducts = await webService.getOrdered(this.$store.state.email);
            } catch (error) {
                console.error(error);
            }
        },
    }
};
</script>

<style>
.list-group-item {
  margin-top: 10px;
}
</style>