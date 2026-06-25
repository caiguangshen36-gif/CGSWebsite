<script setup>
import avatarImg from '../assets/个人照片.jpg'

const education = [
  { year: '2023.09 - 2027.06', school: '广东理工学院', major: '计算机科学与技术', degree: '本科' },
]
</script>

<template>
  <section id="about" class="section">
    <h2 class="section-title">关于我</h2>
    <p class="section-subtitle">专注 Java 后端与高并发系统的学生开发者</p>

    <div class="about-grid">
      <div class="about-avatar glass-card">
        <img :src="avatarImg" alt="蔡广深" class="avatar-img" />
      </div>
      <div class="about-text">
        <p>
          我是一名计算机科学与技术专业的大三学生，专注于 Java 后端开发与高并发系统设计。
          具备扎实的 Spring Boot、MySQL、Redis 技术栈基础，同时对 AI 应用开发
          （RAG 架构、LLM 集成）有深入实践。
        </p>
        <p>
          我相信技术的力量可以解决实际问题，追求用工程化思维构建可靠、高性能的系统。
          目前正在深入探索分布式架构、AI 应用与性能优化领域。
        </p>

        <div class="education">
          <h3>教育经历</h3>
          <div class="timeline">
            <div v-for="(item, i) in education" :key="i" class="timeline-item">
              <div class="timeline-dot"></div>
              <div class="timeline-content">
                <span class="timeline-year">{{ item.year }}</span>
                <h4>{{ item.school }}</h4>
                <p>{{ item.major }}{{ item.degree ? ' · ' + item.degree : '' }}</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.about-grid {
  display: grid;
  grid-template-columns: 260px 1fr;
  gap: 48px;
  align-items: start;
}

.about-avatar {
  aspect-ratio: 1;
  overflow: hidden;
  padding: 0;
}

.avatar-img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.about-text p {
  color: var(--text-secondary);
  margin-bottom: 16px;
  font-size: 1.02rem;
  line-height: 1.8;
}

.education {
  margin-top: 32px;
}

.education h3 {
  font-family: var(--font-mono);
  font-size: 1.15rem;
  margin-bottom: 20px;
  color: var(--text-primary);
}

.timeline {
  position: relative;
  padding-left: 24px;
}

.timeline::before {
  content: '';
  position: absolute;
  left: 8px;
  top: 8px;
  bottom: 8px;
  width: 2px;
  background: var(--border);
}

.timeline-item {
  position: relative;
  margin-bottom: 28px;
}

.timeline-dot {
  position: absolute;
  left: -20px;
  top: 8px;
  width: 10px;
  height: 10px;
  border-radius: 50%;
  background: var(--accent-1);
}

.timeline-content {
  padding-left: 8px;
}

.timeline-year {
  font-family: var(--font-mono);
  font-size: 0.85rem;
  color: var(--accent-3);
}

.timeline-content h4 {
  font-size: 1.05rem;
  margin: 4px 0;
}

.timeline-content p {
  color: var(--text-secondary);
  font-size: 0.95rem;
  margin: 0;
}

@media (max-width: 768px) {
  .about-grid {
    grid-template-columns: 1fr;
  }
  .about-avatar {
    max-width: 200px;
    margin: 0 auto;
  }
}
</style>
