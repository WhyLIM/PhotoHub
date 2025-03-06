<template>
    <div class="explore-view" :style="backgroundStyle">
        <div class="photo-container">
            <img :src="currentPhoto.url" alt="随机照片" class="featured-photo" />
        </div>
        <div class="photo-actions">
            <el-button type="primary" @click="loadRandomPhoto">换一张</el-button>
        </div>
        <div class="photo-details-container">
            <div class="photo-details">
                <h2 class="photo-title">{{ currentPhoto.title }}</h2>
                <p class="photo-story">{{ currentPhoto.story }}</p>

                <div class="exif-info">
                    <h3 class="exif-title">拍摄信息</h3>
                    <div class="exif-grid">
                        <div class="exif-item">
                            <span class="exif-label">相机厂商</span>
                            <span class="exif-value">{{ currentPhoto.exif.make }}</span>
                        </div>
                        <div class="exif-item">
                            <span class="exif-label">相机型号</span>
                            <span class="exif-value">{{ currentPhoto.exif.model }}</span>
                        </div>
                        <div class="exif-item">
                            <span class="exif-label">镜头型号</span>
                            <span class="exif-value">{{ currentPhoto.exif.lens }}</span>
                        </div>
                        <div class="exif-item">
                            <span class="exif-label">焦距</span>
                            <span class="exif-value">{{ currentPhoto.exif.focalLength }}</span>
                        </div>
                        <div class="exif-item">
                            <span class="exif-label">光圈</span>
                            <span class="exif-value">{{ currentPhoto.exif.aperture }}</span>
                        </div>
                        <div class="exif-item">
                            <span class="exif-label">快门速度</span>
                            <span class="exif-value">{{ currentPhoto.exif.shutterSpeed }}</span>
                        </div>
                        <div class="exif-item">
                            <span class="exif-label">ISO</span>
                            <span class="exif-value">{{ currentPhoto.exif.iso }}</span>
                        </div>
                        <div class="exif-item">
                            <span class="exif-label">拍摄日期</span>
                            <span class="exif-value">{{ currentPhoto.exif.dateTaken }}</span>
                        </div>
                    </div>
                </div>

                <div class="tags-container">
                    <h3 class="tags-title">标签</h3>
                    <div class="tags-list">
                        <el-tag v-for="tag in currentPhoto.tags" :key="tag" class="photo-tag" color="#fff0">{{ tag
                            }}</el-tag>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
import { ref, computed } from 'vue'
import { ElButton, ElTag } from 'element-plus'

// 模拟照片数据
const photos = [
    {
        id: 1,
        url: 'https://picsum.photos/id/10/1200/800',
        title: '山间湖泊',
        story: '这张照片拍摄于一个宁静的清晨，湖面如镜，倒映着周围的山峦。云雾缭绕间，大自然展现出它神秘而壮丽的一面。',
        tags: ['风景', '湖泊', '山脉', '自然'],
        exif: {
            make: 'Sony',
            model: 'Alpha A7R IV',
            lens: 'FE 16-35mm F2.8 GM',
            focalLength: '16mm',
            aperture: 'f/16',
            shutterSpeed: '1/125s',
            iso: '400',
            dateTaken: '2023-10-15'
        }
    },
    {
        id: 2,
        url: 'https://picsum.photos/id/11/1200/800',
        title: '海岸日落',
        story: '夕阳西下，金色的阳光洒在海面上，形成了一条闪耀的金色通道。远处的帆船剪影为这幅画面增添了一丝诗意。',
        tags: ['日落', '海洋', '剪影', '自然'],
        exif: {
            make: 'Canon',
            model: 'EOS 5D Mark IV',
            lens: 'EF 24-70mm f/2.8L II USM',
            focalLength: '35mm',
            aperture: 'f/8',
            shutterSpeed: '1/250s',
            iso: '100',
            dateTaken: '2023-09-22'
        }
    },
    {
        id: 3,
        url: 'https://picsum.photos/id/12/1200/800',
        title: '城市夜景',
        story: '繁华都市的夜晚，霓虹灯光勾勒出城市的轮廓。高楼大厦的灯光如同星辰般闪烁，展现出现代都市的活力与魅力。',
        tags: ['城市', '夜景', '建筑', '灯光'],
        exif: {
            make: 'Nikon',
            model: 'Z7 II',
            lens: 'NIKKOR Z 24-70mm f/2.8 S',
            focalLength: '50mm',
            aperture: 'f/4',
            shutterSpeed: '2s',
            iso: '800',
            dateTaken: '2023-11-05'
        }
    }
]

// 当前显示的照片
const currentPhotoIndex = ref(0)
const currentPhoto = computed(() => photos[currentPhotoIndex.value])

// 加载随机照片
const loadRandomPhoto = () => {
    let newIndex
    do {
        newIndex = Math.floor(Math.random() * photos.length)
    } while (newIndex === currentPhotoIndex.value && photos.length > 1)

    currentPhotoIndex.value = newIndex
}

// 背景样式，使用当前照片创建高斯模糊背景
const backgroundStyle = computed(() => ({
    '--bg-image': `url(${currentPhoto.value.url})`,
}))
</script>

<style scoped>
.explore-view {
    position: relative;
    min-height: calc(100vh - 70px - 3rem);
    padding: 2rem 0;
}

.explore-view::before {
    content: '';
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background-image: var(--bg-image);
    background-size: cover;
    background-position: center;
    filter: blur(20px) brightness(0.5);
    opacity: 1;
    z-index: -1;
    transform: scale(1.1);
    /* 避免模糊边缘 */
}

.photo-container {
    /* display: flex; */
    /* flex-direction: column; */
    /* gap: 2rem; */
    /* max-width: 1200px; */
    /* max-height: 500px; */
    /* margin: 0 auto; */
    /* border-radius: 12px; */
    /* overflow: hidden; */
    /* box-shadow: 0 8px 30px rgba(0, 0, 0, 0.2); */
    width: 80%;
    margin: auto;
}

/* .photo-display {
  width: 100%;
  position: relative;
} */

.featured-photo {
    width: 100%;
    height: auto;
    display: block;
    /* max-height: 70vh; */
    object-fit: contain;
    border-radius: 12px;
    overflow: hidden;
    box-shadow: 0 8px 30px rgba(0, 0, 0, 0.2);
}

.photo-actions {
    position: absolute;
    bottom: 1rem;
    right: 1rem;
}

.photo-details-container {
    width: 85%;
    margin: auto;
}

.photo-details {
    padding: 2rem;
}

.photo-title {
    font-size: 2rem;
    margin-bottom: 1rem;
    color: #e1e1e1;
}

.photo-story {
    font-size: 1.1rem;
    line-height: 1.6;
    color: #ffffff;
    margin-bottom: 2rem;
}

.exif-title,
.tags-title {
    font-size: 1.4rem;
    margin-bottom: 1rem;
    color: #e1e1e1;
}

.exif-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
    gap: 1rem;
    margin-bottom: 2rem;
}

.exif-item {
    display: flex;
    flex-direction: column;
    gap: 0.3rem;
}

.exif-label {
    font-size: 0.9rem;
    color: #c1c1c1;
}

.exif-value {
    font-size: 1.1rem;
    color: #ffffff;
    font-weight: 500;
}

.tags-list {
    display: flex;
    flex-wrap: wrap;
    gap: 0.5rem;
}

.el-tag.el-tag--primary {
    color: #ffffff;
}

.photo-tag {
    margin-right: 0.5rem;
}

@media (min-width: 768px) {
    .photo-container {
        flex-direction: row;
    }

    .photo-display {
        flex: 1;
        /* max-width: 60%; */
    }

    .photo-details {
        flex: 1;
        /* max-width: 40%; */
        overflow-y: auto;
        max-height: 70vh;
    }
}
</style>