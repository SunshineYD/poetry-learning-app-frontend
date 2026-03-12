<template>
  <div class="min-h-screen bg-gradient-to-b from-blue-100 to-purple-100 flex flex-col items-center justify-center p-4">
    <div class="w-full max-w-md bg-white rounded-lg shadow-lg p-8 border-4 border-primary">
      <h2 class="text-3xl font-bold text-center text-primary mb-6">登录</h2>
      <form @submit.prevent="handleLogin">
        <div class="mb-4">
          <label for="username" class="block text-gray-700 font-medium mb-2">用户名</label>
          <input 
            type="text" 
            id="username" 
            v-model="username" 
            class="w-full px-4 py-2 border-2 border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-primary focus:border-transparent"
            placeholder="请输入用户名"
            required
          >
        </div>
        <div class="mb-6">
          <label for="password" class="block text-gray-700 font-medium mb-2">密码</label>
          <input 
            type="password" 
            id="password" 
            v-model="password" 
            class="w-full px-4 py-2 border-2 border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-primary focus:border-transparent"
            placeholder="请输入密码"
            required
          >
        </div>
        <button 
          type="submit" 
          class="w-full bg-primary text-white font-bold py-2 px-4 rounded-lg hover:bg-opacity-90 transition-all"
        >
          登录
        </button>
        <div class="mt-4 text-center">
          <p class="text-gray-600">还没有账号？ <router-link to="/register" class="text-primary font-medium">立即注册</router-link></p>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Login',
  data() {
    return {
      username: '',
      password: ''
    }
  },
  methods: {
    handleLogin() {
      // 模拟登录，实际项目中会调用API
      localStorage.setItem('user', JSON.stringify({ username: this.username }))
      this.$router.push('/children')
    }
  }
}
</script>

<style scoped>
/* 额外的样式可以在这里添加 */
</style>