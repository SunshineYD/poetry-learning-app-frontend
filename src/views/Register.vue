<template>
  <div class="min-h-screen bg-gradient-to-b from-blue-100 to-purple-100 flex flex-col items-center justify-center p-4">
    <div class="w-full max-w-md bg-white rounded-lg shadow-lg p-8 border-4 border-secondary">
      <h2 class="text-3xl font-bold text-center text-secondary mb-6">注册</h2>
      <form @submit.prevent="handleRegister">
        <div class="mb-4">
          <label for="username" class="block text-gray-700 font-medium mb-2">用户名</label>
          <input 
            type="text" 
            id="username" 
            v-model="username" 
            class="w-full px-4 py-2 border-2 border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-secondary focus:border-transparent"
            placeholder="请输入用户名"
            required
          >
        </div>
        <div class="mb-4">
          <label for="password" class="block text-gray-700 font-medium mb-2">密码</label>
          <input 
            type="password" 
            id="password" 
            v-model="password" 
            class="w-full px-4 py-2 border-2 border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-secondary focus:border-transparent"
            placeholder="请输入密码"
            required
          >
        </div>
        <div class="mb-6">
          <label for="confirmPassword" class="block text-gray-700 font-medium mb-2">确认密码</label>
          <input 
            type="password" 
            id="confirmPassword" 
            v-model="confirmPassword" 
            class="w-full px-4 py-2 border-2 border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-secondary focus:border-transparent"
            placeholder="请确认密码"
            required
          >
        </div>
        <button 
          type="submit" 
          class="w-full bg-secondary text-white font-bold py-2 px-4 rounded-lg hover:bg-opacity-90 transition-all"
        >
          注册
        </button>
        <div class="mt-4 text-center">
          <p class="text-gray-600">已有账号？ <router-link to="/login" class="text-secondary font-medium">立即登录</router-link></p>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Register',
  data() {
    return {
      username: '',
      password: '',
      confirmPassword: ''
    }
  },
  methods: {
    handleRegister() {
      if (this.password !== this.confirmPassword) {
        alert('密码不一致')
        return
      }
      // 模拟注册，实际项目中会调用API
      localStorage.setItem('user', JSON.stringify({ username: this.username }))
      this.$router.push('/children')
    }
  }
}
</script>

<style scoped>
/* 额外的样式可以在这里添加 */
</style>