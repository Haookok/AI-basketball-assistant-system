<template>
  <div class="detail-container">
    <TopBar />
    <div class="main-content">
      <ClassifyBar />
      <div class="detail-content">
        <!-- 返回按钮 -->
        <div class="back-section">
          <el-button @click="goBack">
            <el-icon><ArrowLeft /></el-icon>
            返回搜索
          </el-button>
        </div>

        <!-- 知识标题区域 -->
        <div class="knowledge-header">
          <h1 class="title">个人防守技巧</h1>
          <div class="meta-info">
            <span class="author">创建者：用户1</span>
            <span class="time">最后修改时间：2020-09-08 12:00</span>
            <div class="stats">
              <span><el-icon><View /></el-icon>291</span>
              <span><el-icon><ThumbsUp /></el-icon>33</span>
              <span><el-icon><Star /></el-icon>33</span>
            </div>
          </div>
          <div class="tags">
            <el-tag>标签1</el-tag>
            <el-tag>标签2</el-tag>
          </div>
        </div>

        <!-- 正文内容 -->
        <div class="content-section">
          <div class="content">
            <!-- 这里是文章内容 -->
          </div>
          
          <!-- 附件区域 -->
          <div class="attachments">
            <div class="attachment-item">
              <el-icon><Document /></el-icon>
              <span>附件1.PDF</span>
            </div>
            <div class="attachment-item">
              <el-icon><Document /></el-icon>
              <span>附件2.xlsx</span>
            </div>
          </div>
        </div>

        <!-- 评论区域 -->
        <div class="comments-section">
          <h3>评论 (11)</h3>
          <div class="comment-list">
            <div class="comment-item">
              <el-avatar size="small">XXX</el-avatar>
              <div class="comment-content">
                <div class="comment-header">
                  <span class="username">XXX</span>
                  <span class="time">12:12(今天不显示日期)</span>
                </div>
                <div class="comment-text">评论1</div>
                <div class="comment-actions">
                  <span><el-icon><ChatLineRound /></el-icon>0</span>
                  <span><el-icon><ThumbsUp /></el-icon>0</span>
                </div>
              </div>
            </div>
          </div>
          
          <!-- 评论输入框 -->
          <div class="comment-input">
            <el-input
              type="textarea"
              v-model="commentText"
              placeholder="输入评论"
              :rows="3"
            />
            <el-button type="primary" class="submit-btn">
              发表评论
            </el-button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import { useRouter } from 'vue-router'
import TopBar from '../components/TopBar.vue'
import ClassifyBar from '../components/ClassifyBar.vue'
import { ArrowLeft, View, ThumbsUp, Star, Document, ChatLineRound } from '@element-plus/icons-vue'

const router = useRouter()
const commentText = ref('')

const goBack = () => {
  router.back()
}
</script>

<style scoped>
.detail-container {
  background-color: #e9f0f8;
  min-height: 100vh;
}

.main-content {
  display: flex;
  padding: 29px 23px;
}

.detail-content {
  flex: 1;
  margin-left: 36px;
  margin-right: 16px;
}

.back-section {
  margin-bottom: 20px;
}

.knowledge-header {
  background-color: white;
  padding: 24px;
  border-radius: 8px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.05);
}

.title {
  font-size: 24px;
  margin: 0 0 16px 0;
}

.meta-info {
  display: flex;
  align-items: center;
  color: #666;
  font-size: 14px;
  margin-bottom: 16px;
}

.meta-info > * {
  margin-right: 20px;
}

.stats {
  display: flex;
  gap: 16px;
}

.stats span {
  display: flex;
  align-items: center;
  gap: 4px;
}

.tags {
  margin-top: 16px;
}

.tags .el-tag {
  margin-right: 8px;
}

.content-section {
  background-color: white;
  margin-top: 20px;
  padding: 24px;
  border-radius: 8px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.05);
}

.attachments {
  margin-top: 20px;
  padding-top: 20px;
  border-top: 1px solid #eee;
}

.attachment-item {
  display: flex;
  align-items: center;
  gap: 8px;
  padding: 8px 0;
  color: #666;
}

.comments-section {
  background-color: white;
  margin-top: 20px;
  padding: 24px;
  border-radius: 8px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.05);
}

.comment-item {
  display: flex;
  gap: 12px;
  padding: 16px 0;
  border-bottom: 1px solid #eee;
}

.comment-content {
  flex: 1;
}

.comment-header {
  margin-bottom: 8px;
}

.username {
  font-weight: bold;
  margin-right: 12px;
}

.time {
  color: #999;
  font-size: 12px;
}

.comment-actions {
  margin-top: 8px;
  display: flex;
  gap: 16px;
  color: #666;
}

.comment-actions span {
  display: flex;
  align-items: center;
  gap: 4px;
  cursor: pointer;
}

.comment-input {
  margin-top: 20px;
}

.submit-btn {
  margin-top: 16px;
  float: right;
}
</style>