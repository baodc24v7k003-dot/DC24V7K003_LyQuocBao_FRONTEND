<template>
  <div class="page" style="max-width: 400px; margin: 60px auto;">
    <h4>Đăng nhập</h4>
    <div class="form-group">
      <label>Username</label>
      <input v-model="username" type="text" class="form-control" />
    </div>
    <div class="form-group">
      <label>Password</label>
      <input v-model="password" type="password" class="form-control" />
    </div>
    <p class="text-danger" v-if="error">{{ error }}</p>
    <button class="btn btn-primary" @click="login">Đăng nhập</button>
  </div>
</template>

<script>
import AuthService from "@/services/auth.service";
export default {
  data() {
    return { username: "", password: "", error: "" };
  },
  methods: {
    async login() {
      try {
        const res = await AuthService.login({
          username: this.username,
          password: this.password,
        });
        localStorage.setItem("token", res.token);
        this.$router.push({ name: "contactbook" });
      } catch (err) {
        this.error = "Sai username hoặc password.";
      }
    },
  },
};
</script>