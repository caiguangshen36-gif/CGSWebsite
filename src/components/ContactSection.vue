<script setup>
const contacts = [
  {
    label: 'Email',
    value: '13680940056@163.com',
    link: 'mailto:13680940056@163.com',
    icon: 'M21.75 6.75v10.5a2.25 2.25 0 01-2.25 2.25h-15a2.25 2.25 0 01-2.25-2.25V6.75m19.5 0A2.25 2.25 0 0019.5 4.5h-15a2.25 2.25 0 00-2.25 2.25m19.5 0v.243a2.25 2.25 0 01-1.07 1.916l-7.5 4.615a2.25 2.25 0 01-2.36 0L3.32 8.91a2.25 2.25 0 01-1.07-1.916V6.75',
  },
  {
    label: 'GitHub',
    value: 'github.com/caiguangshen36-gif',
    link: 'https://github.com/caiguangshen36-gif',
    icon: 'M12 0C5.37 0 0 5.37 0 12c0 5.31 3.435 9.795 8.205 11.385.6.105.825-.255.825-.57 0-.285-.015-1.23-.015-2.235-3.015.555-3.795-.735-4.035-1.41-.135-.345-.72-1.41-1.23-1.695-.42-.225-1.02-.78-.015-.795.945-.015 1.62.87 1.845 1.23 1.08 1.815 2.805 1.305 3.495.99.105-.78.42-1.305.765-1.605-2.67-.3-5.46-1.335-5.46-5.925 0-1.305.465-2.385 1.23-3.225-.12-.3-.54-1.53.12-3.18 0 0 1.005-.315 3.3 1.23.96-.27 1.98-.405 3-.405s2.04.135 3 .405c2.295-1.56 3.3-1.23 3.3-1.23.66 1.65.24 2.88.12 3.18.765.84 1.23 1.905 1.23 3.225 0 4.605-2.805 5.625-5.475 5.925.435.375.81 1.095.81 2.22 0 1.605-.015 2.895-.015 3.3 0 .315.225.69.825.57A12.02 12.02 0 0024 12c0-6.63-5.37-12-12-12z',
  },
  {
    label: '电话',
    value: '13680940056',
    link: 'tel:13680940056',
    icon: 'M2.25 6.75C2.25 15.34 9.16 22.25 17.75 22.25h1.5a2.25 2.25 0 002.25-2.25v-3.75a2.25 2.25 0 00-2.25-2.25h-2.25a2.25 2.25 0 00-2.25 2.25v1.5a10.5 10.5 0 01-7.5-7.5h1.5A2.25 2.25 0 0011.25 5.5V3.25A2.25 2.25 0 009 1H5.25A2.25 2.25 0 003 3.25v1.5c0 .55.45 1 1 1z',
  },
]
</script>

<template>
  <section id="contact" class="section">
    <h2 class="section-title">联系我</h2>
    <p class="section-subtitle">期待与你的交流与合作</p>

    <div class="contact-grid">
      <a
        v-for="c in contacts"
        :key="c.label"
        :href="c.link"
        :target="c.link.startsWith('http') ? '_blank' : undefined"
        :rel="c.link.startsWith('http') ? 'noopener noreferrer' : undefined"
        class="contact-card glass-card"
      >
        <svg class="contact-icon" viewBox="0 0 24 24" fill="currentColor">
          <path :d="c.icon"/>
        </svg>
        <span class="contact-label">{{ c.label }}</span>
        <span class="contact-value">{{ c.value }}</span>
      </a>
    </div>
  </section>
</template>

<style scoped>
.contact-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
  gap: 24px;
}

.contact-card {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 10px;
  padding: 40px 24px;
  text-align: center;
}

.contact-icon {
  width: 36px;
  height: 36px;
  color: var(--accent-1);
  margin-bottom: 8px;
}

.contact-label {
  font-size: 0.9rem;
  color: var(--text-secondary);
}

.contact-value {
  font-family: var(--font-mono);
  font-size: 0.9rem;
  color: var(--text-primary);
  word-break: break-all;
}
</style>
