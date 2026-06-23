<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const roles = ['计算机科学与技术专业学生', 'Java 后端开发者', 'AI 应用探索者', '终身学习者']
const currentRole = ref('')
const roleIndex = ref(0)
const charIndex = ref(0)
const isDeleting = ref(false)
let timer = null

function type() {
  const full = roles[roleIndex.value]
  if (!isDeleting.value) {
    currentRole.value = full.slice(0, charIndex.value + 1)
    charIndex.value++
    if (charIndex.value === full.length) {
      isDeleting.value = true
      timer = setTimeout(type, 2000)
      return
    }
  } else {
    currentRole.value = full.slice(0, charIndex.value - 1)
    charIndex.value--
    if (charIndex.value === 0) {
      isDeleting.value = false
      roleIndex.value = (roleIndex.value + 1) % roles.length
    }
  }
  timer = setTimeout(type, isDeleting.value ? 50 : 100)
}

onMounted(() => { timer = setTimeout(type, 500) })
onUnmounted(() => clearTimeout(timer))
</script>

<template>
  <section id="hero" class="hero">
    <div class="hero-content">
      <p class="hero-greeting">你好，我是</p>
      <h1 class="hero-name">蔡广深</h1>
      <p class="hero-role">
        <span class="typing">{{ currentRole }}</span>
        <span class="cursor">|</span>
      </p>
      <p class="hero-desc">
        热衷于高并发系统设计与 AI 应用开发，用工程化思维解决复杂问题。
      </p>
      <div class="hero-actions">
        <a href="#projects" class="btn-primary">查看作品</a>
        <a href="#contact" class="btn-secondary">联系我</a>
      </div>
    </div>
  </section>
</template>

<style scoped>
.hero {
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
  padding: 24px;
}

.hero-content {
  text-align: center;
  z-index: 1;
  max-width: 700px;
}

.hero-greeting {
  font-family: var(--font-mono);
  color: var(--accent-1);
  font-size: 1.1rem;
  margin-bottom: 16px;
}

.hero-name {
  font-size: clamp(3rem, 8vw, 5rem);
  font-weight: 800;
  line-height: 1.1;
  margin-bottom: 16px;
  color: var(--text-primary);
  letter-spacing: -0.03em;
}

.hero-role {
  font-family: var(--font-mono);
  font-size: 1.3rem;
  color: var(--text-secondary);
  margin-bottom: 20px;
  min-height: 2rem;
}

.typing {
  color: var(--text-primary);
}

.cursor {
  color: var(--accent-1);
  animation: blink 0.8s infinite;
}

@keyframes blink {
  0%, 100% { opacity: 1; }
  50% { opacity: 0; }
}

.hero-desc {
  font-size: 1.15rem;
  color: var(--text-secondary);
  max-width: 500px;
  margin: 0 auto 36px;
  line-height: 1.7;
}

.hero-actions {
  display: flex;
  gap: 16px;
  justify-content: center;
  flex-wrap: wrap;
}

.btn-primary,
.btn-secondary {
  padding: 12px 32px;
  border-radius: 6px;
  font-size: 1rem;
  font-weight: 600;
  transition: opacity 0.2s;
}

.btn-primary {
  background: var(--accent-1);
  color: #fff;
}

.btn-primary:hover {
  opacity: 0.85;
}

.btn-secondary {
  border: 1px solid var(--border);
  color: var(--text-primary);
}

.btn-secondary:hover {
  border-color: var(--accent-1);
}
</style>
