<template>
  <footer class="footer">
    <div class="footer-content">
      <div class="copyright">
        &copy; {{ currentYear }} PhotoHub. 保留所有权利。
      </div>
      <div class="footer-links">
        <a href="#" class="footer-link">关于我们</a>
        <a href="#" class="footer-link">联系方式</a>
        <a href="#" class="footer-link">隐私政策</a>
      </div>
    </div>
  </footer>
</template>

<script setup>
import { computed } from 'vue'

const currentYear = computed(() => new Date().getFullYear())
</script>

<style scoped>
.footer {
  background-color: #f5f5f5;
  padding: 2rem 0;
  margin-top: 3rem;
  border-top: 1px solid rgba(0, 0, 0, 0.1);
}

.footer-content {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 1rem;
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  gap: 1rem;
}

.copyright {
  color: #666;
  font-size: 0.9rem;
}

.footer-links {
  display: flex;
  gap: 1.5rem;
}

.footer-link {
  color: #666;
  text-decoration: none;
  font-size: 0.9rem;
  transition: color 0.3s;
}

.footer-link:hover {
  color: #409EFF;
}

@media (min-width: 768px) {
  .footer-content {
    flex-direction: row;
    justify-content: space-between;
    text-align: left;
  }
}
</style>