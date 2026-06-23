<template>
  <footer class="footer">
    <div class="footer-inner">
      <p class="footer-text">&copy; {{ new Date().getFullYear() }} 蔡广深. Built with Vue &amp; Vite.</p>
    </div>
  </footer>
</template>

<style scoped>
.footer {
  border-top: 1px solid var(--border);
  padding: 32px 24px;
}

.footer-inner {
  max-width: var(--max-width);
  margin: 0 auto;
  text-align: center;
}

.footer-text {
  color: var(--text-secondary);
  font-size: 0.9rem;
}
</style>
