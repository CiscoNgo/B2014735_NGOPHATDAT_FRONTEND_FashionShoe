<template>
  <div class="login-container">
    <img
      src="https://img.freepik.com/free-photo/fashion-shoes-sneaker_1203-8081.jpg?size=626&ext=jpg&ga=GA1.1.167429326.1700706235&semt=ais"
      alt="Hình ảnh giới thiệu"
      class="background-image"
    />
    <div class="login-card">
      <div class="card-body">
        <h3 class="text-center mb-4">Đăng nhập</h3>
        <form @submit.prevent="login">
          <div class="form-group">
            <label for="email">Email:</label>
            <input v-model="email" type="email" placeholder="Nhập vào email" id="email" class="form-control" required />
          </div>
          <div class="form-group">
            <label for="password">Mật khẩu:</label>
            <input v-model="password" type="password" placeholder="Nhập vào mật khẩu" id="password" class="form-control" required />
          </div>
          <div class="forgot-password">
            <a href="#">Quên mật khẩu?</a>
          </div>
          <div class="text-center">
            <button type="submit" class="btn btn-primary">Đăng nhập</button>
          </div>
          <div class="register-link text-center">
            Bạn chưa có tài khoản?
            <a href="#"><i>Đăng ký</i></a>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
import webService from '../services/web.service';

export default {
  data() {
    return {
      email: '',
      password: '',
      users: [],
    };
  },
  created() {
    this.fetchProducts();
  },
  methods: {
    async fetchProducts() {
      try {
        this.users = await webService.getAcountUser();
      } catch (error) {
        console.error(error);
      }
    },

    login() {
      const checkUser = this.users.find((user) => user.email === this.email);
      if (checkUser && checkUser.password === this.password) {
        this.$store.commit('login', this.email);
        if (this.email === 'admin@gmail.com') {
          this.$router.push('/admin');
        } else {
          this.$router.push('/');
        }
      } else {
        alert('Sai thông tin tài khoản');
      }
    },
  },
};
</script>

<style>
.login-container {
  position: relative;
  margin-top: 5%;
}

.background-image {
  max-width: 100%;
  display: block;
  margin: 0 auto;
}

.login-card {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 350px;
  background-color: #fff;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  border-radius: 10px;
}

.card-body {
  padding: 20px;
}

.form-group {
  margin-bottom: 20px;
}

label {
  display: block;
  font-weight: bold;
  margin-bottom: 5px;
}

input {
  width: 100%;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 5px;
}

.forgot-password {
  float: right;
}

.btn-primary {
  background-color: #007bff;
  color: #fff;
  padding: 14px 20px;
  margin-top: 8px;
  border: none;
  cursor: pointer;
  width: 100%;
  border-radius: 5px;
  transition: background-color 0.3s;
}

.btn-primary:hover {
  background-color: #0056b3;
}

.register-link {
  margin-top: 10px;
}

.register-link a {
  color: #007bff;
}
</style>
