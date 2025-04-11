<template>
    <div class="home-view" :style="backgroundStyle">
        <div class="profile-section">
            <div class="avatar-container">
                <img src="/avatar.png" alt="个人头像" class="avatar-image" />
                <div class="social-icons">
                    <a href="https://instagram.com" target="_blank" class="social-icon">
                        <font-awesome-icon :icon="['fab', 'instagram']" />
                    </a>
                    <a href="https://weibo.com" target="_blank" class="social-icon">
                        <font-awesome-icon :icon="['fab', 'weibo']" />
                    </a>
                    <a href="https://github.com" target="_blank" class="social-icon">
                        <font-awesome-icon :icon="['fab', 'github']" />
                    </a>
                    <a href="https://twitter.com" target="_blank" class="social-icon">
                        <font-awesome-icon :icon="['fab', 'twitter']" />
                    </a>
                </div>
            </div>
            <div class="bio-container">
                <h1 class="bio-title">欢迎来到 PhotoHub</h1>
                <h2 class="bio-subtitle">摄影师 & 旅行爱好者</h2>
                <p class="bio-text">
                    热爱摄影的旅行者，喜欢用镜头记录世界各地的美景和人文风情。
                    擅长风光和街头摄影，希望通过照片分享我眼中的世界。
                </p>
                <p class="bio-text">
                    这是一个展示精选摄影作品的平台，记录光与影的瞬间，分享摄影的乐趣与感动。
                    在这里，您可以欣赏到各种风格的摄影作品，了解每张照片背后的故事和技术细节。
                </p>
                <div class="navigation-buttons">
                    <router-link to="/explore" class="nav-button explore-button">探索作品</router-link>
                    <router-link to="/collections" class="nav-button collections-button">浏览影像集</router-link>
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
    flex: 1;
    flex-direction: column;
    gap: 2rem;
    padding: 8rem 0;
    max-width: 1200px;
    margin: 0 auto;
    min-height: calc(100vh - 150px); /* 减去导航栏和页脚的高度 */
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

.profile-section {
    display: flex;
    flex-direction: column;
    gap: 2rem;
    background: rgba(255, 255, 255, 0.9);
    border-radius: 12px;
    padding: 2rem;
    box-shadow: 0 8px 24px rgba(0, 0, 0, 0.12);
}

.avatar-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 1.5rem;
}

.avatar-image {
    width: 200px;
    height: 200px;
    border-radius: 50%;
    object-fit: cover;
    border: 4px solid white;
    box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
    transition: transform 0.3s ease;
}

.avatar-image:hover {
    transform: scale(1.05);
}

.social-icons {
    display: flex;
    gap: 1.2rem;
    margin-top: 0.5rem;
}

.social-icon {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 40px;
    height: 40px;
    border-radius: 50%;
    background: #f5f5f5;
    color: #555;
    font-size: 1.2rem;
    transition: all 0.3s ease;
}

.social-icon:hover {
    background: #409EFF;
    color: white;
    transform: translateY(-3px);
}

.bio-container {
    display: flex;
    flex-direction: column;
}

.bio-title {
    font-size: 2.2rem;
    margin-bottom: 0.5rem;
    color: #333;
}

.bio-subtitle {
    font-size: 1.3rem;
    color: #666;
    margin-bottom: 1.5rem;
    font-weight: 500;
}

.bio-text {
    font-size: 1.1rem;
    line-height: 1.6;
    color: #555;
    margin-bottom: 1rem;
}

.navigation-buttons {
    display: flex;
    gap: 1rem;
    margin-top: 1.5rem;
}

.nav-button {
    display: inline-block;
    padding: 0.8rem 1.5rem;
    border-radius: 6px;
    font-size: 1rem;
    font-weight: 500;
    text-decoration: none;
    transition: all 0.3s ease;
}

.explore-button {
    background: #409EFF;
    color: white;
}

.collections-button {
    background: transparent;
    color: #409EFF;
    border: 1px solid #409EFF;
}

.nav-button:hover {
    transform: translateY(-3px);
    box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
}

.explore-button:hover {
    background: #2c8af8;
}

.collections-button:hover {
    background: rgba(64, 158, 255, 0.1);
}

@media (min-width: 768px) {
    .profile-section {
        flex-direction: row;
        align-items: flex-start;
        margin: auto;
    }

    .avatar-container {
        flex: 1;
        max-width: 300px;
        margin: auto;
    }

    .bio-container {
        flex: 2;
        padding-left: 2rem;
    }
}

@media (max-width: 767px) {
    .home-view {
        padding: 1rem;
    }

    .profile-section {
        padding: 1.5rem;
    }

    .avatar-image {
        width: 150px;
        height: 150px;
    }

    .bio-title {
        font-size: 1.8rem;
    }

    .bio-subtitle {
        font-size: 1.1rem;
    }

    .navigation-buttons {
        flex-direction: column;
    }
}
</style>
