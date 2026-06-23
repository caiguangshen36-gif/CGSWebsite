<script setup>
import { ref, inject, onMounted, onUnmounted } from 'vue'

const activeSection = inject('activeSection')
const mobileOpen = ref(false)

const links = [
  { id: 'hero', label: '首页' },
  { id: 'about', label: '关于我' },
  { id: 'skills', label: '技能' },
  { id: 'projects', label: '项目' },
  { id: 'contact', label: '联系' },
]

function scrollTo(id) {
  mobileOpen.value = false
  document.getElementById(id)?.scrollIntoView({ behavior: 'smooth' })
}

let observer = null

onMounted(() => {
  const sections = links.map(l => document.getElementById(l.id)).filter(Boolean)
  observer = new IntersectionObserver(
    (entries) => {
      const visible = entries.filter(e => e.isIntersecting)
      if (visible.length) {
        activeSection.value = visible[0].target.id
      }
    },
    { threshold: 0.3, rootMargin: '-64px 0px -50% 0px' }
  )
  sections.forEach(s => observer.observe(s))
})

onUnmounted(() => {
  observer?.disconnect()
})
</script>

<template>
  <nav class="navbar">
    <div class="nav-inner">
      <a href="#" class="nav-logo" @click.prevent="scrollTo('hero')">
        &lt;CS /&gt;
      </a>
      <button
        class="hamburger"
        :class="{ open: mobileOpen }"
        @click="mobileOpen = !mobileOpen"
        aria-label="Toggle menu"
      >
        <span></span><span></span><span></span>
      </button>
      <ul class="nav-links" :class="{ open: mobileOpen }">
        <li v-for="link in links" :key="link.id">
          <a
            :href="'#' + link.id"
            :class="{ active: activeSection === link.id }"
            @click.prevent="scrollTo(link.id)"
          >
            {{ link.label }}
          </a>
        </li>
      </ul>
    </div>
  </nav>
</template>

<style scoped>
.navbar {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 1000;
  height: var(--nav-height);
  background: rgba(13, 17, 23, 0.9);
  backdrop-filter: blur(12px);
  border-bottom: 1px solid var(--border);
}

.nav-inner {
  max-width: var(--max-width);
  margin: 0 auto;
  padding: 0 24px;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.nav-logo {
  font-family: var(--font-mono);
  font-size: 1.25rem;
  font-weight: 700;
  color: var(--accent-1);
}

.nav-links {
  display: flex;
  gap: 32px;
}

.nav-links a {
  font-size: 0.95rem;
  color: var(--text-secondary);
  padding: 8px 0;
  border-bottom: 2px solid transparent;
  transition: color 0.2s, border-color 0.2s;
}

.nav-links a:hover,
.nav-links a.active {
  color: var(--text-primary);
  border-bottom-color: var(--accent-1);
}

/* Hamburger */
.hamburger {
  display: none;
  flex-direction: column;
  gap: 5px;
  background: none;
  border: none;
  cursor: pointer;
  padding: 4px;
}

.hamburger span {
  display: block;
  width: 24px;
  height: 2px;
  background: var(--text-primary);
  border-radius: 2px;
  transition: transform 0.3s, opacity 0.3s;
}

.hamburger.open span:nth-child(1) {
  transform: translateY(7px) rotate(45deg);
}

.hamburger.open span:nth-child(2) {
  opacity: 0;
}

.hamburger.open span:nth-child(3) {
  transform: translateY(-7px) rotate(-45deg);
}

@media (max-width: 768px) {
  .hamburger {
    display: flex;
  }

  .nav-links {
    position: fixed;
    top: var(--nav-height);
    left: 0;
    right: 0;
    flex-direction: column;
    gap: 0;
    background: rgba(13, 17, 23, 0.95);
    backdrop-filter: blur(12px);
    border-bottom: 1px solid var(--border);
    padding: 16px 24px;
    transform: translateY(-100%);
    opacity: 0;
    pointer-events: none;
    transition: transform 0.3s, opacity 0.3s;
  }

  .nav-links.open {
    transform: translateY(0);
    opacity: 1;
    pointer-events: auto;
  }

  .nav-links a {
    display: block;
    padding: 14px 0;
    border-bottom: 1px solid var(--border);
  }

  .nav-links a.active {
    border-bottom-color: var(--accent-1);
  }
}
</style>
