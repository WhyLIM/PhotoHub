<script setup>
import { RouterLink } from 'vue-router'
</script>

<template>
    <header class="header">
        <div class="header-content">
            <div class="logo-container">
                <img alt="PhotoHub logo" class="logo" src="@/assets/logo.svg" />
            </div>
            <nav class="nav-menu">
                <RouterLink to="/" class="nav-item">首页</RouterLink>
                <RouterLink to="/explore" class="nav-item">探索</RouterLink>
                <RouterLink to="/collections" class="nav-item">影像集</RouterLink>
            </nav>
        </div>
    </header>
</template>

<style scoped>
.header {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    z-index: 100;
    opacity: 0.8;
    background: rgba(255, 255, 255, 0.95);
    backdrop-filter: blur(10px);
    border-bottom: 1px solid rgba(0, 0, 0, 0.1);
}

.header-content {
    max-width: 1200px;
    margin: 0 auto;
    padding: 1rem;
    display: flex;
    align-items: center;
    justify-content: space-between;
}

.logo-container {
    display: flex;
    align-items: center;
}

.logo {
    height: 40px;
    width: auto;
}

.nav-menu {
    display: flex;
    gap: 2rem;
}

.nav-item {
    text-decoration: none;
    color: #333;
    font-size: 1rem;
    font-weight: 500;
    transition: color 0.3s;
}

.nav-item:hover,
.nav-item.router-link-active {
    color: #409EFF;
}
</style>