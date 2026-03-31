<template>
  <a-layout class="app-layout" :class="{ 'dark-mode': isDark }">
    <header class="navbar" :class="{ 'scrolled': isScrolled }">
      <div class="navbar-content">
        <router-link to="/" class="logo">
          <img src="@/assets/logo.png" alt="Logo" class="logo-img" />
        </router-link>
        
        <nav class="nav-menu" :class="{ 'mobile-open': mobileMenuOpen }">
          <router-link to="/" class="nav-link" @click="closeMobileMenu">Home</router-link>
          <router-link to="/about" class="nav-link" @click="closeMobileMenu">About</router-link>
          <router-link to="/contact" class="nav-link" @click="closeMobileMenu">Contact</router-link>
        </nav>

        <div class="nav-actions">
          <button class="theme-toggle" @click="toggleTheme" :title="isDark ? 'Light Mode' : 'Dark Mode'">
            <BulbOutlined v-if="!isDark" />
            <BulbFilled v-else />
          </button>
          <button class="mobile-menu-btn" @click="mobileMenuOpen = !mobileMenuOpen">
            <MenuOutlined v-if="!mobileMenuOpen" />
            <CloseOutlined v-else />
          </button>
        </div>
      </div>
    </header>

    <a-layout-content class="main-content">
      <router-view v-slot="{ Component }">
        <transition name="fade" mode="out-in">
          <component :is="Component" :is-dark="isDark" />
        </transition>
      </router-view>
    </a-layout-content>

    <footer class="footer">
      <div class="footer-content">
        <div class="social-links">
          <a href="mailto:annemarizdelacruz@gmail.com" class="social-link" title="Email">
            <MailOutlined />
          </a>
          <a href="https://linkedin.com/in/amadc" target="_blank" rel="noopener noreferrer" class="social-link" title="LinkedIn">
            <LinkedinOutlined />
          </a>
        </div>
        <p class="copyright">© {{ new Date().getFullYear() }} Anne Mariz Dela Cruz. All rights reserved.</p>
      </div>
    </footer>
  </a-layout>
</template>

<script lang="ts">
import { defineComponent, ref, onMounted, onUnmounted } from "vue";
import { 
  BulbOutlined,
  BulbFilled,
  MenuOutlined, 
  CloseOutlined,
  MailOutlined,
  LinkedinOutlined
} from "@ant-design/icons-vue";

export default defineComponent({
  name: "App",
  components: {
    BulbOutlined,
    BulbFilled,
    MenuOutlined,
    CloseOutlined,
    MailOutlined,
    LinkedinOutlined
  },
  setup() {
    const isDark = ref(false);
    const mobileMenuOpen = ref(false);
    const isScrolled = ref(false);

    const toggleTheme = () => {
      isDark.value = !isDark.value;
      localStorage.setItem('theme', isDark.value ? 'dark' : 'light');
      document.documentElement.setAttribute('data-theme', isDark.value ? 'dark' : 'light');
    };

    const closeMobileMenu = () => {
      mobileMenuOpen.value = false;
    };

    const handleScroll = () => {
      isScrolled.value = window.scrollY > 20;
    };

    onMounted(() => {
      const savedTheme = localStorage.getItem('theme');
      if (savedTheme) {
        isDark.value = savedTheme === 'dark';
      } else {
        isDark.value = window.matchMedia('(prefers-color-scheme: dark)').matches;
      }
      document.documentElement.setAttribute('data-theme', isDark.value ? 'dark' : 'light');
      window.addEventListener('scroll', handleScroll);
    });

    onUnmounted(() => {
      window.removeEventListener('scroll', handleScroll);
    });

    return {
      isDark,
      mobileMenuOpen,
      isScrolled,
      toggleTheme,
      closeMobileMenu
    };
  },
});
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800&display=swap');

:root {
  --color-primary: #ff69b4;
  --color-primary-hover: #ff85c8;
  --color-bg: #fff5f5;
  --color-bg-secondary: #fff0f5;
  --color-bg-card: #ffffff;
  --color-text: #5d4e60;
  --color-text-secondary: #9a8a9a;
  --color-border: #ffd1dc;
  --glass-bg: rgba(255, 245, 245, 0.8);
  --glass-border: rgba(255, 209, 220, 0.3);
  --shadow-sm: 0 1px 2px rgba(255, 182, 193, 0.2);
  --shadow-md: 0 4px 6px -1px rgba(255, 182, 193, 0.3);
  --shadow-lg: 0 10px 15px -3px rgba(255, 182, 193, 0.3);
  --shadow-xl: 0 20px 25px -5px rgba(255, 182, 193, 0.3);
  --gradient-primary: linear-gradient(135deg, #ff69b4 0%, #ff85c8 100%);
  --gradient-bg: linear-gradient(135deg, #fff5f5 0%, #fff0f5 100%);
}

[data-theme="dark"] {
  --color-bg: #1a1625;
  --color-bg-secondary: #2d2640;
  --color-bg-card: #352945;
  --color-text: #f0e6ee;
  --color-text-secondary: #b8a4b8;
  --color-border: #4a3f5c;
  --glass-bg: rgba(45, 38, 64, 0.8);
  --glass-border: rgba(74, 63, 92, 0.3);
  --shadow-sm: 0 1px 2px rgba(0, 0, 0, 0.3);
  --shadow-md: 0 4px 6px -1px rgba(0, 0, 0, 0.4);
  --shadow-lg: 0 10px 15px -3px rgba(0, 0, 0, 0.4);
  --shadow-xl: 0 20px 25px -5px rgba(0, 0, 0, 0.4);
  --gradient-bg: linear-gradient(135deg, #1a1625 0%, #2d2640 100%);
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
  background: var(--color-bg);
  color: var(--color-text);
  line-height: 1.6;
  transition: background-color 0.3s ease, color 0.3s ease;
}

.app-layout {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  background: var(--gradient-bg);
}

.navbar {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 1000;
  padding: 1rem 2rem;
  transition: all 0.3s ease;
  background: transparent;
}

.navbar.scrolled {
  background: var(--glass-bg);
  backdrop-filter: blur(12px);
  -webkit-backdrop-filter: blur(12px);
  border-bottom: 1px solid var(--glass-border);
  box-shadow: var(--shadow-md);
}

.navbar-content {
  max-width: 1200px;
  margin: 0 auto;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.logo {
  display: flex;
  align-items: center;
  text-decoration: none;
}

.logo-img {
  height: 40px;
  width: auto;
  object-fit: contain;
}

.nav-menu {
  display: flex;
  gap: 0.5rem;
}

.nav-link {
  padding: 0.625rem 1.25rem;
  text-decoration: none;
  color: var(--color-text);
  font-weight: 500;
  border-radius: 8px;
  transition: all 0.2s ease;
}

.nav-link:hover {
  color: var(--color-primary);
  background: rgba(255, 105, 180, 0.1);
}

.nav-link.router-link-active {
  color: var(--color-primary);
  background: rgba(255, 105, 180, 0.1);
}

.nav-actions {
  display: flex;
  align-items: center;
  gap: 0.75rem;
}

.theme-toggle {
  width: 40px;
  height: 40px;
  border-radius: 10px;
  border: none;
  background: var(--color-bg-card);
  color: var(--color-text);
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 1.125rem;
  transition: all 0.2s ease;
  box-shadow: var(--shadow-sm);
}

.theme-toggle:hover {
  background: var(--color-primary);
  color: white;
  transform: scale(1.05);
}

.mobile-menu-btn {
  display: none;
  width: 40px;
  height: 40px;
  border-radius: 10px;
  border: none;
  background: var(--color-bg-card);
  color: var(--color-text);
  cursor: pointer;
  font-size: 1.25rem;
}

.main-content {
  flex: 1;
  padding-top: 80px;
}

.footer {
  background: var(--color-bg-secondary);
  border-top: 1px solid var(--color-border);
  padding: 2rem;
  margin-top: auto;
}

.footer-content {
  max-width: 1200px;
  margin: 0 auto;
  text-align: center;
}

.social-links {
  display: flex;
  justify-content: center;
  gap: 1rem;
  margin-bottom: 1rem;
}

.social-link {
  width: 44px;
  height: 44px;
  border-radius: 12px;
  display: flex;
  align-items: center;
  justify-content: center;
  background: var(--color-bg-card);
  color: var(--color-text);
  font-size: 1.25rem;
  transition: all 0.2s ease;
  box-shadow: var(--shadow-sm);
  text-decoration: none;
}

.social-link:hover {
  background: var(--color-primary);
  color: white;
  transform: translateY(-3px);
  box-shadow: var(--shadow-md);
}

.copyright {
  color: var(--color-text-secondary);
  font-size: 0.875rem;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.25s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

@media (max-width: 768px) {
  .navbar {
    padding: 1rem;
  }

  .nav-menu {
    position: fixed;
    top: 72px;
    left: 0;
    right: 0;
    background: var(--glass-bg);
    backdrop-filter: blur(12px);
    flex-direction: column;
    padding: 1rem;
    gap: 0.5rem;
    transform: translateY(-100%);
    opacity: 0;
    pointer-events: none;
    transition: all 0.3s ease;
    border-bottom: 1px solid var(--glass-border);
  }

  .nav-menu.mobile-open {
    transform: translateY(0);
    opacity: 1;
    pointer-events: auto;
  }

  .nav-link {
    padding: 0.875rem 1rem;
    border-radius: 10px;
  }

  .mobile-menu-btn {
    display: flex;
    align-items: center;
    justify-content: center;
  }
}
</style>