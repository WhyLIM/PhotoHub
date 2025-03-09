<template>
  <div class="collections-view" :style="backgroundStyle">
    <h1 class="collections-title">影像集</h1>
    <div class="collections-grid">
      <div v-for="collection in collections" :key="collection.id" class="collection-card"
        @click="viewCollection(collection)">
        <div class="collection-cover">
          <img :src="collection.coverImage" :alt="collection.title" class="cover-image" />
          <div class="collection-info">
            <h3 class="collection-title">{{ collection.title }}</h3>
            <p class="collection-description">{{ collection.description }}</p>
            <div class="collection-meta">
              <span class="photo-count">{{ collection.photoCount }}张照片</span>
              <span class="collection-date">{{ collection.date }}</span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'

// 背景样式，使用当前照片创建高斯模糊背景
const backgroundStyle = computed(() => ({
  '--bg-image': `url(https://picsum.photos/600/800)`,
}))

// 模拟合集数据
const collections = ref([
  {
    id: 1,
    title: '自然风光',
    description: '记录大自然的壮丽景色，从雄伟的山脉到宁静的湖泊。',
    coverImage: 'https://picsum.photos/id/10/800/600',
    photoCount: 12,
    date: '2023-10'
  },
  {
    id: 2,
    title: '城市剪影',
    description: '探索现代都市的建筑之美与人文风情。',
    coverImage: 'https://picsum.photos/id/11/800/600',
    photoCount: 8,
    date: '2023-11'
  },
  {
    id: 3,
    title: '日落时分',
    description: '捕捉黄昏时分的绚丽色彩与温暖光线。',
    coverImage: 'https://picsum.photos/id/12/800/600',
    photoCount: 15,
    date: '2023-12'
  }
])

// 查看合集详情
const viewCollection = (collection) => {
  // TODO: 实现查看合集详情的功能
  console.log('查看合集:', collection.title)
}
</script>

<style scoped>
.collections-view {
  padding: 2rem 0;
}

.collections-view::before {
  content: '';
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-image: var(--bg-image);
  background-size: cover;
  background-position: center;
  filter: blur(20px) brightness(0.7);
  opacity: 1;
  z-index: -1;
  transform: scale(1.1);
  /* 避免模糊边缘 */
}

.collections-title {
  font-size: 2.5rem;
  margin-bottom: 2rem;
  color: #fff;
}

.collections-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  gap: 2rem;
}

.collection-card {
  background: white;
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  cursor: pointer;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.collection-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.15);
}

.collection-cover {
  position: relative;
  padding-bottom: 75%;
  overflow: hidden;
}

.cover-image {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.3s ease;
}

.collection-card:hover .cover-image {
  transform: scale(1.05);
}

.collection-info {
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  padding: 1.5rem;
  background: linear-gradient(to top, rgba(0, 0, 0, 0.8), transparent);
  color: white;
}

.collection-title {
  font-size: 1.4rem;
  margin-bottom: 0.5rem;
}

.collection-description {
  font-size: 0.9rem;
  margin-bottom: 1rem;
  opacity: 0.9;
}

.collection-meta {
  display: flex;
  justify-content: space-between;
  font-size: 0.8rem;
  opacity: 0.8;
}
</style>
