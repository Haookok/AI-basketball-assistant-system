<template>
    <div class="home-container">
        <TopBar />
        <div class="search-results-container">
            <div class="search-header">
                <h2>搜索结果</h2>
                <p>搜索关键词：{{ keyword }}</p>
            </div>
        
            <div class="knowledge-list" v-if="knowledgeList.length">
                <div class="knowledge-item" v-for="(item, index) in knowledgeList" :key="index">
                <h3>{{ item.title }}</h3>
                <p>{{ item.description }}</p>
                </div>
            </div>
            <div v-else>
                <p>没有找到相关的知识。</p>
            </div>
        </div>
    </div>
  </template>
  
  <script setup>
  import TopBar from '../components/TopBar.vue'
  import { ref, onMounted } from 'vue'
  import { useRoute } from 'vue-router'
  import axios from 'axios'
  
  const route = useRoute()
  const keyword = route.query.keyword || ''
  const knowledgeList = ref([])
  
  const fetchKnowledge = async () => {
    try {
      const response = await axios.get('/api/knowledge/search', {
        params: { query: keyword }
      })
      knowledgeList.value = response.data || []
    } catch (error) {
      console.error('获取知识列表失败', error)
    }
  }
  
  onMounted(() => {
    if (keyword) {
      fetchKnowledge()
    }
  })
  </script>
  
  <style scoped>
  .search-results-container {
    padding: 20px;
    background-color: #f9f9f9;
    border-radius: 10px;
  }
  
  .search-header {
    margin-bottom: 20px;
    text-align: center;
  }
  
  .knowledge-list {
    display: flex;
    flex-direction: column;
    gap: 10px;
  }
  
  .knowledge-item {
    padding: 10px;
    background-color: #fff;
    border-radius: 8px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  }
  
  .knowledge-item h3 {
    margin: 0;
    font-size: 18px;
  }
  
  .knowledge-item p {
    font-size: 14px;
    color: #666;
  }
  </style>
  