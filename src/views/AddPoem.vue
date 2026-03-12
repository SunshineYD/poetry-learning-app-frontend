<template>
  <div class="min-h-screen bg-gradient-to-b from-blue-100 to-purple-100 p-4">
    <div class="max-w-4xl mx-auto">
      <div class="flex justify-between items-center mb-6">
        <h1 class="text-3xl font-bold text-primary">添加诗歌</h1>
        <router-link to="/poems" class="bg-gray-500 text-white font-bold py-2 px-4 rounded-lg hover:bg-opacity-90 transition-all">
          返回
        </router-link>
      </div>
      
      <div class="bg-white rounded-lg shadow-lg p-8 border-4 border-accent">
        <form @submit.prevent="addPoem">
          <div class="mb-4">
            <label for="title" class="block text-gray-700 font-medium mb-2">诗歌标题</label>
            <input 
              type="text" 
              id="title" 
              v-model="newPoem.title" 
              class="w-full px-4 py-2 border-2 border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-accent focus:border-transparent"
              placeholder="请输入诗歌标题"
              required
            >
          </div>
          <div class="mb-4">
            <label for="author" class="block text-gray-700 font-medium mb-2">作者</label>
            <input 
              type="text" 
              id="author" 
              v-model="newPoem.author" 
              class="w-full px-4 py-2 border-2 border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-accent focus:border-transparent"
              placeholder="请输入作者姓名"
              required
            >
          </div>
          <div class="mb-6">
            <label for="content" class="block text-gray-700 font-medium mb-2">诗歌内容</label>
            <textarea 
              id="content" 
              v-model="newPoem.content" 
              rows="4" 
              class="w-full px-4 py-2 border-2 border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-accent focus:border-transparent"
              placeholder="请输入诗歌内容"
              required
            ></textarea>
          </div>
          <button 
            type="submit" 
            class="w-full bg-accent text-white font-bold py-2 px-4 rounded-lg hover:bg-opacity-90 transition-all"
          >
            添加诗歌
          </button>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'AddPoem',
  data() {
    return {
      newPoem: {
        title: '',
        author: '',
        content: ''
      }
    }
  },
  methods: {
    addPoem() {
      // 模拟添加诗歌，实际项目中会调用API
      alert('诗歌添加成功！')
      this.$router.push('/poems')
    }
  }
}
</script>

<style scoped>
/* 额外的样式可以在这里添加 */
</style>