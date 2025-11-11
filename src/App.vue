<template>
  <div id="app" :class="{ 'dark-mode': isDarkMode }">
    <Navigation
      :isDarkMode="isDarkMode"
      :currentLang="currentLang"
      :translations="translations"
      @toggle-dark-mode="toggleDarkMode"
      @change-language="changeLanguage"
    />
    <main>
      <Hero :translations="translations" />
      <About :translations="translations" />
      <Portfolio :translations="translations" />
      <Contact :translations="translations" />
    </main>
    <Footer :translations="translations" />
  </div>
</template>

<script>
import Navigation from './components/Navigation.vue'
import Hero from './components/Hero.vue'
import About from './components/About.vue'
import Portfolio from './components/Portfolio.vue'
import Contact from './components/Contact.vue'
import Footer from './components/Footer.vue'
import { translations as allTranslations } from './translations.js'

export default {
  name: 'App',
  components: {
    Navigation,
    Hero,
    About,
    Portfolio,
    Contact,
    Footer
  },
  data() {
    return {
      isDarkMode: true, // Dark mode is enabled by default
      currentLang: 'en' // Default language is English
    }
  },
  computed: {
    translations() {
      return allTranslations[this.currentLang]
    }
  },
  mounted() {
    // Apply dark mode to body element
    this.applyDarkMode()
  },
  methods: {
    toggleDarkMode() {
      this.isDarkMode = !this.isDarkMode
      this.applyDarkMode()
    },
    applyDarkMode() {
      if (this.isDarkMode) {
        document.body.classList.add('dark-mode')
      } else {
        document.body.classList.remove('dark-mode')
      }
    },
    changeLanguage(lang) {
      this.currentLang = lang
    }
  }
}
</script>

<style>
/* Global styles are in style.css */
</style>
