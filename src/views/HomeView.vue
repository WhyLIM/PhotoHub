<template>
    <div class="home-view" :style="backgroundStyle">
        <div class="welcome-section">
            <h1 class="welcome-title">欢迎来到 PhotoHub</h1>
            <p class="welcome-text">
                这是一个展示精选摄影作品的平台，记录光与影的瞬间，分享摄影的乐趣与感动。
                在这里，您可以欣赏到各种风格的摄影作品，了解每张照片背后的故事和技术细节。
            </p>
            <p class="welcome-text">
                通过导航栏，您可以探索随机精选的照片，或浏览按主题组织的影像集。
                每张照片都附有详细的拍摄参数和创作故事，希望能为您带来视觉上的享受和摄影技术上的启发。
            </p>
        </div>
        <div class="daily-photo-section">
            <h2 class="section-title">每日推荐</h2>
            <div class="photo-card">
                <img src="https://picsum.photos/600/800" alt="每日推荐照片" class="featured-photo" />
                <div class="photo-info">
                    <h3 class="photo-title">山间湖泊</h3>
                    <p class="photo-description">宁静的湖水倒映着雄伟的山峰，云雾缭绕间展现大自然的神秘与壮丽。</p>
                    <div class="photo-meta">
                        <span class="photo-date">拍摄于 2023年10月15日</span>
                        <span class="photo-location">奥地利 哈尔施塔特</span>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
import { computed } from 'vue'
// 这里可以添加获取随机照片的逻辑

// 背景样式，使用当前照片创建高斯模糊背景
const backgroundStyle = computed(() => ({
    '--bg-image': `url(https://picsum.photos/600/800)`,
}))
</script>

<style scoped>
.home-view {
  display: flex;
  flex-direction: column;
  gap: 2rem;
  padding: 2rem 0;
}

.home-view::before {
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

.welcome-title {
  font-size: 2.5rem;
  margin-bottom: 1.5rem;
  color: #333;
}

.welcome-text {
  font-size: 1.1rem;
  line-height: 1.6;
  color: #555;
  margin-bottom: 1rem;
}

.section-title {
  font-size: 1.8rem;
  margin-bottom: 1.5rem;
  color: #333;
}

.photo-card {
  background: white;
  border-radius: 8px;
  overflow: hidden;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s ease;
}

.photo-card:hover {
  transform: translateY(-5px);
}

.featured-photo {
  width: 100%;
  height: auto;
  object-fit: cover;
  display: block;
}

.photo-info {
  padding: 1.5rem;
}

.photo-title {
  font-size: 1.4rem;
  margin-bottom: 0.5rem;
  color: #333;
}

.photo-description {
  font-size: 1rem;
  color: #555;
  margin-bottom: 1rem;
  line-height: 1.5;
}

.photo-meta {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
  font-size: 0.9rem;
  color: #777;
}

@media (min-width: 768px) {
  .home-view {
    flex-direction: row;
    align-items: flex-start;
  }
  
  .welcome-section {
    flex: 1;
    padding-right: 2rem;
  }
  
  .daily-photo-section {
    flex: 1;
  }
}
</style>
