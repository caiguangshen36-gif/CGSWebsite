<script setup>
const skillGroups = [
  {
    name: '语言 / 框架',
    skills: [
      { name: 'Java', level: 90 },
      { name: 'Spring Boot 3.x', level: 88 },
      { name: 'MyBatis-Plus', level: 85 },
      { name: 'Spring Security', level: 78 },
    ],
  },
  {
    name: '数据库 / 缓存',
    skills: [
      { name: 'MySQL（索引优化 / 事务 / 锁）', level: 75 },
      { name: 'Redis（缓存策略 / Lua / 分布式锁）', level: 70 },
    ],
  },
  {
    name: 'AI 应用',
    skills: [
      { name: 'Spring AI + RAG 架构', level: 82 },
      { name: 'Prompt Engineering', level: 70 },
      { name: '向量检索 / LLM 集成', level: 70 },
    ],
  },
  {
    name: 'AI 工具',
    skills: [
      { name: 'Claude Code', level: 85 },
      { name: 'Trae', level: 75 },
      { name: '通义千问', level: 78 },
      { name: 'DeepSeek', level: 80 },
    ],
  },
  {
    name: '工具 / 其他',
    skills: [
      { name: 'JMeter 压测', level: 60 },
      { name: 'Git', level: 70 },
      { name: '数据结构与算法', level: 78 },
    ],
  },
]
</script>

<template>
  <section id="skills" class="section">
    <h2 class="section-title">技能</h2>
    <p class="section-subtitle">持续学习与积累的技术栈</p>

    <div class="skills-grid">
      <div v-for="group in skillGroups" :key="group.name" class="skill-group glass-card">
        <h3 class="group-title">{{ group.name }}</h3>
        <div class="skill-list">
          <div v-for="skill in group.skills" :key="skill.name" class="skill-item">
            <div class="skill-info">
              <span class="skill-name">{{ skill.name }}</span>
              <span class="skill-pct">{{ skill.level }}%</span>
            </div>
            <div class="skill-bar">
              <div
                class="skill-fill"
                :style="{ width: skill.level + '%' }"
              ></div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.skills-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 24px;
}

.skill-group {
  padding: 28px;
}

.group-title {
  font-family: var(--font-mono);
  font-size: 1.1rem;
  margin-bottom: 24px;
  color: var(--accent-3);
}

.skill-list {
  display: flex;
  flex-direction: column;
  gap: 18px;
}

.skill-info {
  display: flex;
  justify-content: space-between;
  margin-bottom: 6px;
  font-size: 0.95rem;
}

.skill-pct {
  font-family: var(--font-mono);
  color: var(--text-secondary);
  font-size: 0.85rem;
}

.skill-bar {
  height: 6px;
  background: rgba(255, 255, 255, 0.05);
  border-radius: 3px;
  overflow: hidden;
}

.skill-fill {
  height: 100%;
  border-radius: 3px;
  background: var(--accent-1);
  transition: width 1s ease;
}
</style>
