<template>
    <div class="container">
    <h1 class="my-6" style="text-align: center;">Welcome to Admin</h1>
    <div class="row">
      <div class="col-md-6">
        <div class="card">
          <img src="https://toperp.vn/web/image/65949-b68f846a/4433108.jpg?access_token=f198386f-ccd7-427d-9522-f7b983db4709" width="300" height="250" class="card-img-top" alt="Ảnh minh họa">
          <div class="card-body">
            <h5 class="card-title">Quản lý Sản phẩm</h5>
            <p class="card-text">Quản lý danh sách sản phẩm, thêm, sửa, xóa sản phẩm.</p>
            <a href="/admin/product" class="btn btn-primary">Đến trang quản lý sản phẩm</a>
          </div>
        </div>
      </div>
      <div class="col-md-6">
        <div class="card">
          <img src="https://cdn-kvweb.kiotviet.vn/kiotviet-website/wp-content/uploads/2018/04/nhung-dieu-nhan-vien-quan-ly-don-hang-shop-ban-le-can-biet.jpg" width="300" height="250" class="card-img-top" alt="Ảnh minh họa">
          <div class="card-body">
            <h5 class="card-title">Quản lý Đơn hàng</h5>
            <p class="card-text">Quản lý đơn hàng, xác nhận, giao hàng, và hủy đơn hàng.</p>
            <a href="/admin/order" class="btn btn-primary">Đến trang quản lý đơn hàng</a>
          </div>
        </div>
      </div>
    </div>
  </div>    
</template>

<style>
/* Tùy chỉnh kiểu dáng cho phù hợp với giao diện của trang chủ admin */
.card {
  margin-top: 20px;
  box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
  transition: 0.3s;
}

.card:hover {
  box-shadow: 0 8px 16px 0 rgba(0,0,0,0.2);
}
</style>