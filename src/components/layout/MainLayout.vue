<template>
  <div class="main-layout">
    <TheHeader />
    <main class="content">
      <slot></slot>
    </main>
    <TheFooter />
  </div>
</template>

<script setup>
import TheHeader from './TheHeader.vue'
import TheFooter from './TheFooter.vue'
</script>

<style scoped>
.main-layout {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}

.content {
  flex: 1;
  padding-top: 70px; /* 为固定的header留出空间 */
  max-width: 1200px;
  width: 100%;
  margin: 0 auto;
  padding-left: 1rem;
  padding-right: 1rem;
}
</style>