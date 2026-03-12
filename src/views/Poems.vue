<template>
  <div class="min-h-screen bg-gradient-to-b from-blue-100 to-purple-100 p-4">
    <div class="max-w-4xl mx-auto">
      <div class="flex justify-between items-center mb-6">
        <h1 class="text-3xl font-bold text-primary">诗歌管理</h1>
        <router-link to="/add-poem" class="bg-accent text-white font-bold py-2 px-4 rounded-lg hover:bg-opacity-90 transition-all flex items-center gap-2">
          <span>➕</span> 添加诗歌
        </router-link>
      </div>
      
      <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
        <div v-for="poem in poems" :key="poem.id" class="bg-white rounded-lg shadow-md p-6 border-4 border-secondary">
          <div class="flex justify-between items-center mb-4">
            <h3 class="text-xl font-bold text-secondary">{{ poem.title }}</h3>
            <span class="text-sm text-gray-500">{{ poem.author }}</span>
          </div>
          <div class="mb-4">
            <p class="text-gray-600 line-clamp-3">{{ poem.content }}</p>
          </div>
          <div class="flex justify-between items-center">
            <span class="text-sm text-gray-500">熟悉度: {{ poem.familiarity }}%</span>
            <button @click="toggleCheckin(poem.id)" class="bg-primary text-white font-bold py-1 px-3 rounded-lg hover:bg-opacity-90 transition-all text-sm">
              {{ poem.checkedIn ? '已打卡' : '打卡' }}
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Poems',
  data() {
    return {
      poems: [
        {
          id: 1,
          title: '静夜思',
          author: '李白',
          content: '床前明月光，疑是地上霜。举头望明月，低头思故乡。',
          familiarity: 80,
          checkedIn: true
        },
        {
          id: 2,
          title: '春晓',
          author: '孟浩然',
          content: '春眠不觉晓，处处闻啼鸟。夜来风雨声，花落知多少。',
          familiarity: 60,
          checkedIn: false
        },
        {
          id: 3,
          title: '望庐山瀑布',
          author: '李白',
          content: '日照香炉生紫烟，遥看瀑布挂前川。飞流直下三千尺，疑是银河落九天。',
          familiarity: 40,
          checkedIn: false
        }
      ]
    }
  },
  methods: {
    toggleCheckin(id) {
      const poem = this.poems.find(p => p.id === id)
      if (poem) {
        poem.checkedIn = !poem.checkedIn
        if (poem.checkedIn) {
          poem.familiarity = Math.min(100, poem.familiarity + 10)
        }
      }
    }
  }
}
</script>

<style scoped>
.line-clamp-3 {
  display: -webkit-box;
  -webkit-line-clamp: 3;
  -webkit-box-orient: vertical;
  overflow: hidden;
}
</style>