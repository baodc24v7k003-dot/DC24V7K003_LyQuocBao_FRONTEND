<template>
  <nav class="navbar navbar-expand navbar-dark bg-dark">
    <a href="/" class="navbar-brand">Ứng dụng Quản lý danh bạ</a>
    <div class="mr-auto navbar-nav">
      <li class="nav-item">
        <router-link :to="{ name: 'contactbook' }" class="nav-link">
          Danh bạ
          <i class="fas fa-address-book"></i>
        </router-link>
      </li>
    </div>
    <div class="navbar-nav ml-auto">
      <button class="btn btn-outline-light btn-sm" @click="logout">
        <i class="fas fa-sign-out-alt"></i> Đăng xuất
      </button>
    </div>
  </nav>
</template>

<script>
export default {
  methods: {
    logout() {
      if (confirm("Bạn có muốn đăng xuất không?")) {
        localStorage.removeItem("token");
        this.$router.push({ name: "login" });
      }
    },
  },
};
</script>