<template>
  <div class="min-h-screen bg-gradient-to-b from-blue-100 to-purple-100 p-4">
    <div class="max-w-4xl mx-auto">
      <div class="flex justify-between items-center mb-6">
        <h1 class="text-3xl font-bold text-primary">孩子管理</h1>
        <button @click="showAddChildModal = true" class="bg-primary text-white font-bold py-2 px-4 rounded-lg hover:bg-opacity-90 transition-all flex items-center gap-2">
          <span>➕</span> 添加孩子
        </button>
      </div>
      
      <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
        <div v-for="child in children" :key="child.id" class="bg-white rounded-lg shadow-md p-6 border-4 border-primary">
          <div class="flex justify-between items-center mb-4">
            <h3 class="text-xl font-bold text-primary">{{ child.name }}</h3>
            <span class="text-sm text-gray-500">{{ child.age }}岁</span>
          </div>
          <div class="mb-4">
            <span class="text-gray-600">已学习诗歌: {{ child.learnedPoems }}</span>
          </div>
          <div class="flex gap-2">
            <router-link :to="`/poems?childId=${child.id}`" class="flex-1 bg-secondary text-white font-bold py-2 px-4 rounded-lg hover:bg-opacity-90 transition-all text-center">
              查看诗歌
            </router-link>
            <button @click="deleteChild(child.id)" class="bg-red-500 text-white font-bold py-2 px-4 rounded-lg hover:bg-opacity-90 transition-all">
              删除
            </button>
          </div>
        </div>
      </div>
    </div>
    
    <!-- 添加孩子模态框 -->
    <div v-if="showAddChildModal" class="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center p-4">
      <div class="bg-white rounded-lg shadow-lg p-8 border-4 border-primary max-w-md w-full">
        <h2 class="text-2xl font-bold text-center text-primary mb-6">添加孩子</h2>
        <form @submit.prevent="addChild">
          <div class="mb-4">
            <label for="childName" class="block text-gray-700 font-medium mb-2">姓名</label>
            <input 
              type="text" 
              id="childName" 
              v-model="newChild.name" 
              class="w-full px-4 py-2 border-2 border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-primary focus:border-transparent"
              placeholder="请输入孩子姓名"
              required
            >
          </div>
          <div class="mb-6">
            <label for="childAge" class="block text-gray-700 font-medium mb-2">年龄</label>
            <input 
              type="number" 
              id="childAge" 
              v-model="newChild.age" 
              class="w-full px-4 py-2 border-2 border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-primary focus:border-transparent"
              placeholder="请输入孩子年龄"
              required
            >
          </div>
          <div class="flex gap-4">
            <button 
              type="button" 
              @click="showAddChildModal = false" 
              class="flex-1 bg-gray-300 text-gray-700 font-bold py-2 px-4 rounded-lg hover:bg-gray-400 transition-all"
            >
              取消
            </button>
            <button 
              type="submit" 
              class="flex-1 bg-primary text-white font-bold py-2 px-4 rounded-lg hover:bg-opacity-90 transition-all"
            >
              添加
            </button>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Children',
  data() {
    return {
      showAddChildModal: false,
      newChild: {
        name: '',
        age: ''
      },
      children: [
        { id: 1, name: '小明', age: 6, learnedPoems: 5 },
        { id: 2, name: '小红', age: 8, learnedPoems: 12 }
      ]
    }
  },
  methods: {
    addChild() {
      const child = {
        id: this.children.length + 1,
        name: this.newChild.name,
        age: this.newChild.age,
        learnedPoems: 0
      }
      this.children.push(child)
      this.showAddChildModal = false
      this.newChild = { name: '', age: '' }
    },
    deleteChild(id) {
      this.children = this.children.filter(child => child.id !== id)
    }
  }
}
</script>

<style scoped>
/* 额外的样式可以在这里添加 */
</style>