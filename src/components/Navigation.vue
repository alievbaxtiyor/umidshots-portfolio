<template>
  <nav class="navbar" :class="{ 'navbar-scrolled': isScrolled }">
    <div class="container nav-container">
      <a href="#home" class="logo">
        <span class="logo-text">UMIDSHOTS</span>
      </a>

      <button class="menu-toggle" @click="toggleMenu" :class="{ active: isMenuOpen }">
        <span></span>
        <span></span>
        <span></span>
      </button>

      <ul class="nav-menu" :class="{ active: isMenuOpen }">
        <li><a href="#home" @click="closeMenu">{{ translations.nav.home }}</a></li>
        <li><a href="#about" @click="closeMenu">{{ translations.nav.about }}</a></li>
        <li><a href="#portfolio" @click="closeMenu">{{ translations.nav.portfolio }}</a></li>
        <li><a href="#contact" @click="closeMenu">{{ translations.nav.contact }}</a></li>
        <li class="nav-controls">
          <div class="language-selector">
            <button
              v-for="lang in languages"
              :key="lang.code"
              @click="changeLang(lang.code)"
              :class="{ active: currentLang === lang.code }"
              class="lang-btn"
            >
              {{ lang.label }}
            </button>
          </div>
          <button class="theme-toggle" @click="toggleTheme" :title="isDarkMode ? 'Switch to light mode' : 'Switch to dark mode'">
            <svg v-if="isDarkMode" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <circle cx="12" cy="12" r="5"></circle>
              <line x1="12" y1="1" x2="12" y2="3"></line>
              <line x1="12" y1="21" x2="12" y2="23"></line>
              <line x1="4.22" y1="4.22" x2="5.64" y2="5.64"></line>
              <line x1="18.36" y1="18.36" x2="19.78" y2="19.78"></line>
              <line x1="1" y1="12" x2="3" y2="12"></line>
              <line x1="21" y1="12" x2="23" y2="12"></line>
              <line x1="4.22" y1="19.78" x2="5.64" y2="18.36"></line>
              <line x1="18.36" y1="5.64" x2="19.78" y2="4.22"></line>
            </svg>
            <svg v-else width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <path d="M21 12.79A9 9 0 1 1 11.21 3 7 7 0 0 0 21 12.79z"></path>
            </svg>
          </button>
        </li>
      </ul>
    </div>
  </nav>
</template>

<script>
export default {
  name: 'Navigation',
  props: {
    isDarkMode: {
      type: Boolean,
      default: true
    },
    currentLang: {
      type: String,
      default: 'en'
    },
    translations: {
      type: Object,
      required: true
    }
  },
  data() {
    return {
      isScrolled: false,
      isMenuOpen: false,
      languages: [
        { code: 'en', label: 'EN' },
        { code: 'ru', label: 'RU' },
        { code: 'uz', label: 'UZ' }
      ]
    }
  },
  mounted() {
    window.addEventListener('scroll', this.handleScroll)
  },
  beforeUnmount() {
    window.removeEventListener('scroll', this.handleScroll)
  },
  methods: {
    handleScroll() {
      this.isScrolled = window.scrollY > 50
    },
    toggleMenu() {
      this.isMenuOpen = !this.isMenuOpen
    },
    closeMenu() {
      this.isMenuOpen = false
    },
    toggleTheme() {
      this.$emit('toggle-dark-mode')
    },
    changeLang(lang) {
      this.$emit('change-language', lang)
      this.closeMenu()
    }
  }
}
</script>

<style scoped>
.navbar {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 1000;
  padding: 1.5rem 0;
  transition: all 0.3s ease;
  background: transparent;
}

.navbar-scrolled {
  background: rgba(255, 255, 255, 0.95);
  backdrop-filter: blur(10px);
  padding: 1rem 0;
  box-shadow: 0 5px 20px rgba(0, 0, 0, 0.05);
}

.dark-mode .navbar-scrolled {
  background: rgba(26, 26, 26, 0.95);
  box-shadow: 0 5px 20px rgba(255, 255, 255, 0.05);
}

.nav-container {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.logo-text {
  font-size: 1.5rem;
  font-weight: 800;
  letter-spacing: 2px;
  background: var(--gradient);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.nav-menu {
  display: flex;
  list-style: none;
  gap: 2.5rem;
  align-items: center;
}

.nav-menu a {
  text-decoration: none;
  color: var(--text-dark);
  font-weight: 500;
  font-size: 1rem;
  position: relative;
  transition: color 0.3s ease;
}

.nav-menu a::after {
  content: '';
  position: absolute;
  bottom: -5px;
  left: 0;
  width: 0;
  height: 2px;
  background: var(--gradient);
  transition: width 0.3s ease;
}

.nav-menu a:hover {
  color: #667eea;
}

.nav-menu a:hover::after {
  width: 100%;
}

.menu-toggle {
  display: none;
  flex-direction: column;
  background: none;
  border: none;
  cursor: pointer;
  padding: 0.5rem;
  z-index: 1001;
}

.menu-toggle span {
  width: 25px;
  height: 3px;
  background: var(--text-dark);
  margin: 3px 0;
  transition: all 0.3s ease;
  border-radius: 3px;
}

.theme-toggle {
  background: none;
  border: none;
  color: var(--text-dark);
  cursor: pointer;
  padding: 0.5rem;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 50%;
  transition: all 0.3s ease;
}

.theme-toggle:hover {
  background: rgba(102, 126, 234, 0.1);
  transform: rotate(20deg);
}

.theme-toggle svg {
  transition: all 0.3s ease;
}

.nav-controls {
  display: flex;
  align-items: center;
  gap: 1rem;
}

.language-selector {
  display: flex;
  gap: 0.25rem;
  background: rgba(102, 126, 234, 0.1);
  padding: 0.25rem;
  border-radius: 20px;
}

.lang-btn {
  background: none;
  border: none;
  color: var(--text-dark);
  cursor: pointer;
  padding: 0.4rem 0.75rem;
  border-radius: 15px;
  font-size: 0.85rem;
  font-weight: 600;
  transition: all 0.3s ease;
}

.lang-btn:hover {
  background: rgba(102, 126, 234, 0.2);
}

.lang-btn.active {
  background: var(--gradient);
  color: white;
}

.menu-toggle.active span:nth-child(1) {
  transform: rotate(45deg) translate(8px, 8px);
}

.menu-toggle.active span:nth-child(2) {
  opacity: 0;
}

.menu-toggle.active span:nth-child(3) {
  transform: rotate(-45deg) translate(8px, -8px);
}

/* Mobile styles */
@media (max-width: 768px) {
  .menu-toggle {
    display: flex;
  }

  .nav-menu {
    position: fixed;
    top: 0;
    right: -100%;
    width: 70%;
    max-width: 300px;
    height: 100vh;
    background: rgba(255, 255, 255, 0.98);
    backdrop-filter: blur(20px);
    flex-direction: column;
    justify-content: center;
    padding: 2rem;
    gap: 2rem;
    transition: right 0.3s ease;
    box-shadow: -5px 0 20px rgba(0, 0, 0, 0.1);
  }

  .dark-mode .nav-menu {
    background: rgba(26, 26, 26, 0.98);
    box-shadow: -5px 0 20px rgba(255, 255, 255, 0.1);
  }

  .nav-menu.active {
    right: 0;
  }

  .nav-menu a {
    font-size: 1.5rem;
  }

  .nav-controls {
    flex-direction: column;
    width: 100%;
  }

  .language-selector {
    width: 100%;
    justify-content: center;
  }

  .lang-btn {
    flex: 1;
    font-size: 1rem;
    padding: 0.6rem 1rem;
  }

  .theme-toggle {
    margin: 0 auto;
  }
}

@media (max-width: 480px) {
  .logo-text {
    font-size: 1.25rem;
  }

  .nav-menu {
    width: 80%;
  }
}
</style>
