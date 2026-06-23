<script setup>
const projects = [
  {
    title: '智能电商平台（Spring AI）',
    desc: '集成 Spring AI 的全栈电商系统。多策略智能客服（意图识别→DB直查→RAG检索→LLM兜底），自建RAG知识库支持7类文档管理；智能导购引擎覆盖8档价格区间、30+品类；AI文案生成支持6种风格×5种类型；智能搜索（拼写纠错+同义词扩展）。多级缓存+JWT+三阶段库存锁支撑高并发，P99从320ms降至48ms。',
    tags: ['Spring Boot', 'Spring AI', 'MyBatis-Plus', 'MySQL', 'Redis', 'JWT'],
    github: 'https://github.com/caiguangshen36-gif/e_commerce.git',
    demo: 'http://8.163.124.200',
  },
  {
    title: '高并发秒杀系统',
    desc: '从零搭建高并发秒杀系统，完成3阶段6轮JMeter压测（累计156万+请求），定位修复7个关键缺陷。多级缓存（Cache-Aside+预热）将列表页P99从1308ms降至23ms；Lua脚本原子库存扣减配合动态限流，峰值QPS 777稳定运行；定时扫描兜底实现超时订单自动取消与库存双写恢复，全周期0超卖/0重复订单。',
    tags: ['Spring Boot', 'MyBatis-Plus', 'Redis', 'JMeter', 'Lua'],
    github: 'https://github.com/caiguangshen36-gif/seckill-system.git',
    demo: 'http://8.163.136.37',
  },
]
</script>

<template>
  <section id="projects" class="section">
    <h2 class="section-title">项目作品</h2>
    <p class="section-subtitle">实践是最好的学习方式</p>

    <div class="projects-grid">
      <article v-for="p in projects" :key="p.title" class="project-card glass-card">
        <div class="project-img">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1">
            <path d="M2.25 12.75V12A2.25 2.25 0 014.5 9.75h15A2.25 2.25 0 0121.75 12v.75m-8.69-6.44l-2.12-2.12a1.5 1.5 0 00-1.061-.44H4.5A2.25 2.25 0 002.25 6v12a2.25 2.25 0 002.25 2.25h15A2.25 2.25 0 0021.75 18V9a2.25 2.25 0 00-2.25-2.25h-5.379a1.5 1.5 0 01-1.06-.44z"/>
          </svg>
        </div>
        <div class="project-body">
          <h3>{{ p.title }}</h3>
          <p>{{ p.desc }}</p>
          <div class="project-tags">
            <span v-for="t in p.tags" :key="t" class="tag">{{ t }}</span>
          </div>
          <div class="project-links">
            <a :href="p.github" target="_blank">GitHub →</a>
            <a v-if="p.demo !== '#'" :href="p.demo" target="_blank">Demo →</a>
          </div>
        </div>
      </article>
    </div>
  </section>
</template>

<style scoped>
.projects-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
  gap: 24px;
}

.project-card {
  overflow: hidden;
}

.project-img {
  height: 180px;
  display: flex;
  align-items: center;
  justify-content: center;
  background: rgba(88, 166, 255, 0.06);
  color: var(--text-secondary);
  opacity: 0.4;
}

.project-img svg {
  width: 60px;
  height: 60px;
}

.project-body {
  padding: 24px;
}

.project-body h3 {
  font-size: 1.15rem;
  margin-bottom: 10px;
}

.project-body p {
  color: var(--text-secondary);
  font-size: 0.95rem;
  line-height: 1.7;
  margin-bottom: 16px;
}

.project-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  margin-bottom: 18px;
}

.tag {
  font-family: var(--font-mono);
  font-size: 0.78rem;
  padding: 4px 10px;
  border-radius: 6px;
  background: rgba(88, 166, 255, 0.12);
  color: var(--accent-3);
}

.project-links {
  display: flex;
  gap: 20px;
}

.project-links a {
  font-size: 0.9rem;
  color: var(--accent-1);
  transition: color 0.2s;
}

.project-links a:hover {
  color: var(--accent-3);
}
</style>
