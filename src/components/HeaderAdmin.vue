<template>
    <header class="admin-header">
      <nav class="navbar navbar-expand-lg navbar-light bg-light">
        <div class="container">
          <router-link to="/admin/dashboard" class="navbar-brand">Admin Dashboard</router-link>
          <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
            <span class="navbar-toggler-icon"></span>
          </button>
          <div class="collapse navbar-collapse" id="navbarSupportedContent">
            <ul class="navbar-nav me-auto mb-2 mb-lg-0">
              <li class="nav-item">
                <router-link to="/admin/products" class="nav-link">Sản phẩm</router-link>
              </li>
              <li class="nav-item">
                <router-link to="/admin/orders" class="nav-link">Đơn hàng</router-link>
              </li>
              <li class="nav-item">
                <router-link to="/admin/customers" class="nav-link">Khách hàng</router-link>
              </li>
            </ul>
            <form class="d-flex">
              <input class="form-control me-2" type="search" placeholder="Tìm kiếm" aria-label="Search">
              <button class="btn btn-outline-success" type="submit">Tìm kiếm</button>
            </form>
          </div>
        </div>
      </nav>
    </header>
  </template>