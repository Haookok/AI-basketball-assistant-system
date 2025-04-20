<template>
    <div class="classify-bar">
      <div class="title">全部分类</div>
      <el-menu
        class="el-menu-vertical-demo"
        background-color="#fff"
        text-color="#333"
        active-text-color="#ccc"
      >
        <el-sub-menu
          v-for="(item, index) in menuItems"
          :key="index"
          :index="String(index)"
        >
          <template #title>
            <el-icon :size="16">
              <component :is="item.icon" />
            </el-icon>
            <span class="menu-label">{{ item.label }}</span>
          </template>
        </el-sub-menu>
      </el-menu>
    </div>
  </template>
  
  <script setup>
  import {
    Position,
    Basketball,
    Share,
    Aim,
    TakeawayBox,
    Switch,
    User,
    UserFilled,
  } from '@element-plus/icons-vue'
  
  const menuItems = [
    { label: '身体控制和移动技术', icon: Position },
    { label: '运球技术', icon: Basketball },
    { label: '传接球技术', icon: Share },
    { label: '投篮技术', icon: Aim },
    { label: '篮板球技术', icon: TakeawayBox },
    { label: '一对一攻防战术', icon: Switch },
    { label: '二对二攻防战术', icon: User },
    { label: '三对三攻防战术', icon: UserFilled },
  ]
  </script>
  
  <style scoped>
  .classify-bar {
    width: 290px;
    height: 770px;
    background-color: #fff;
    padding: 13px;
    border-radius: 6px;
    box-shadow: 0 0 5px rgba(0, 0, 0, 0.1);
  }
  .title {
    font-weight: bold;
    font-size: 16px;
    margin-bottom: 10px;
  }
  .menu-label {
    margin-left: 8px;
  }
  ::v-deep(.el-menu-item:hover),
  ::v-deep(.el-sub-menu__title:hover) {
    background-color:#f6f6f6!important;
    color: inherit !important;
  }
  </style>
  