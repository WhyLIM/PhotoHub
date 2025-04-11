# PhotoHub 摄影作品展示平台

## 项目简介
基于 Vue3 和 Element Plus 构建的现代摄影作品展示平台，提供摄影作品展示、随机推荐、分类浏览和高清图片查看功能。

## 功能特性
- 作品分类展示（自然/人像/街拍）
- 响应式网格布局
- EXIF元数据展示
- 高清大图查看器
- 用户互动（点赞/收藏）
- 作品上传与管理后台

## 技术栈
### 前端
- Vue 3 + Vite
- Pinia状态管理
- Vue Router
- Element Plus UI
- Axios

## 二次开发指引

克隆本仓库

```sh
# 安装依赖
pnpm install

# 启动开发服务器
pnpm dev

# 构建生产版本
pnpm build
```

## 项目结构

```
src/
├── views/         # 页面组件
│   ├── HomeView.vue      # 首页
│   ├── ExploreView.vue   # 发现
│   └── CollectionsView.vue # 精选
├── components/    # 通用组件
│   ├── Gallery/   # 画廊组件
│   └── Lightbox/  # 大图查看器
└── stores/        # Pinia存储
    └── gallery.js # 作品数据管理
```

## 许可证
MIT License
