<template>
  <footer class="footer">
    <div class="container">
      <div class="footer-content">
        <div class="footer-brand">
          <h3 class="footer-logo">UMIDSHOTS</h3>
          <p>{{ translations.footer.tagline }}</p>
        </div>

        <div class="footer-links">
          <div class="footer-column">
            <h4>{{ translations.footer.navigation }}</h4>
            <ul>
              <li><a href="#home">{{ translations.nav.home }}</a></li>
              <li><a href="#about">{{ translations.nav.about }}</a></li>
              <li><a href="#portfolio">{{ translations.nav.portfolio }}</a></li>
              <li><a href="#contact">{{ translations.nav.contact }}</a></li>
            </ul>
          </div>

          <div class="footer-column">
            <h4>{{ translations.footer.services }}</h4>
            <ul>
              <li><a href="#portfolio">{{ translations.footer.servicesList.photography }}</a></li>
              <li><a href="#portfolio">{{ translations.footer.servicesList.videography }}</a></li>
              <li><a href="#portfolio">{{ translations.footer.servicesList.contentCreation }}</a></li>
              <li><a href="#portfolio">{{ translations.footer.servicesList.editing }}</a></li>
            </ul>
          </div>

          <div class="footer-column">
            <h4>{{ translations.footer.connect }}</h4>
            <ul>
              <li><a href="#">{{ translations.footer.social.instagram }}</a></li>
              <li><a href="#">{{ translations.footer.social.youtube }}</a></li>
              <li><a href="#">{{ translations.footer.social.tiktok }}</a></li>
              <li><a href="#">{{ translations.footer.social.twitter }}</a></li>
            </ul>
          </div>
        </div>
      </div>

      <div class="footer-bottom">
        <p>&copy; {{ currentYear }} UMIDSHOTS. {{ translations.footer.copyright }}.</p>
        <p class="made-with">{{ translations.footer.madeWith }}</p>
      </div>
    </div>
  </footer>
</template>

<script>
export default {
  name: 'Footer',
  props: {
    translations: {
      type: Object,
      required: true
    }
  },
  computed: {
    currentYear() {
      return new Date().getFullYear()
    }
  }
}
</script>

<style scoped>
.footer {
  background: linear-gradient(135deg, #1a1a2e 0%, #16213e 100%);
  color: white;
  padding: 4rem 0 2rem;
}

.dark-mode .footer {
  background: linear-gradient(135deg, #0a0a0a 0%, #1a1a1a 100%);
}

.footer-content {
  display: grid;
  grid-template-columns: 1.5fr 2fr;
  gap: 4rem;
  margin-bottom: 3rem;
  padding-bottom: 3rem;
  border-bottom: 1px solid rgba(255, 255, 255, 0.1);
}

.footer-brand {
  max-width: 350px;
}

.footer-logo {
  font-size: 1.75rem;
  font-weight: 800;
  letter-spacing: 2px;
  background: var(--gradient);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  margin-bottom: 1rem;
}

.footer-brand p {
  color: rgba(255, 255, 255, 0.7);
  font-size: 1rem;
  line-height: 1.6;
}

.footer-links {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 2rem;
}

.footer-column h4 {
  font-size: 1.125rem;
  font-weight: 700;
  margin-bottom: 1.25rem;
  color: white;
}

.footer-column ul {
  list-style: none;
}

.footer-column li {
  margin-bottom: 0.75rem;
}

.footer-column a {
  color: rgba(255, 255, 255, 0.7);
  text-decoration: none;
  font-size: 0.95rem;
  transition: all 0.3s ease;
  display: inline-block;
}

.footer-column a:hover {
  color: white;
  transform: translateX(5px);
}

.footer-bottom {
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-wrap: wrap;
  gap: 1rem;
}

.footer-bottom p {
  color: rgba(255, 255, 255, 0.6);
  font-size: 0.9rem;
}

.made-with {
  font-weight: 500;
}

/* Responsive */
@media (max-width: 1024px) {
  .footer-content {
    grid-template-columns: 1fr;
    gap: 3rem;
  }

  .footer-brand {
    max-width: 100%;
  }

  .footer-links {
    gap: 3rem;
  }
}

@media (max-width: 768px) {
  .footer {
    padding: 3rem 0 2rem;
  }

  .footer-content {
    gap: 2.5rem;
    margin-bottom: 2rem;
    padding-bottom: 2rem;
  }

  .footer-links {
    grid-template-columns: repeat(2, 1fr);
    gap: 2rem;
  }

  .footer-bottom {
    flex-direction: column;
    text-align: center;
    gap: 0.5rem;
  }
}

@media (max-width: 480px) {
  .footer {
    padding: 2.5rem 0 1.5rem;
  }

  .footer-links {
    grid-template-columns: 1fr;
    gap: 2rem;
  }

  .footer-logo {
    font-size: 1.5rem;
  }
}
</style>
