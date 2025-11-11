<template>
  <section id="about" class="about">
    <div class="container">
      <div class="about-grid">
        <div class="about-image">
          <div class="image-wrapper">
            <div class="image-placeholder">
              <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                <rect x="3" y="3" width="18" height="18" rx="2" ry="2"></rect>
                <circle cx="8.5" cy="8.5" r="1.5"></circle>
                <polyline points="21 15 16 10 5 21"></polyline>
              </svg>
              <p>Your Photo Here</p>
            </div>
          </div>
          <div class="decorative-element"></div>
        </div>

        <div class="about-content">
          <p class="section-subtitle">{{ translations.about.subtitle }}</p>
          <h2 class="section-title">{{ translations.about.title }}</h2>
          <p class="about-text">
            {{ translations.about.text1 }}
          </p>
          <p class="about-text">
            {{ translations.about.text2 }}
          </p>

          <div class="skills">
            <div class="skill-item">
              <div class="skill-icon">📱</div>
              <h4>{{ translations.about.skill1Title }}</h4>
              <p>{{ translations.about.skill1Desc }}</p>
            </div>
            <div class="skill-item">
              <div class="skill-icon">🎬</div>
              <h4>{{ translations.about.skill2Title }}</h4>
              <p>{{ translations.about.skill2Desc }}</p>
            </div>
            <div class="skill-item">
              <div class="skill-icon">✨</div>
              <h4>{{ translations.about.skill3Title }}</h4>
              <p>{{ translations.about.skill3Desc }}</p>
            </div>
            <div class="skill-item">
              <div class="skill-icon">🎨</div>
              <h4>{{ translations.about.skill4Title }}</h4>
              <p>{{ translations.about.skill4Desc }}</p>
            </div>
          </div>

          <a href="#contact" class="btn btn-primary">{{ translations.about.workTogether }}</a>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'About',
  props: {
    translations: {
      type: Object,
      required: true
    }
  }
}
</script>

<style scoped>
.about {
  padding: 8rem 0;
  background: linear-gradient(180deg, #ffffff 0%, #f9f9f9 100%);
}

.dark-mode .about {
  background: linear-gradient(180deg, #0a0a0a 0%, #1a1a1a 100%);
}

.about-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 6rem;
  align-items: center;
}

.about-image {
  position: relative;
}

.image-wrapper {
  position: relative;
  border-radius: 20px;
  overflow: hidden;
  aspect-ratio: 4/5;
  box-shadow: 0 30px 60px rgba(0, 0, 0, 0.15);
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
}

.image-placeholder {
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  color: white;
  gap: 1rem;
}

.image-placeholder svg {
  width: 80px;
  height: 80px;
  opacity: 0.8;
}

.image-placeholder p {
  font-size: 1rem;
  color: white;
  opacity: 0.9;
}

.decorative-element {
  position: absolute;
  top: -20px;
  right: -20px;
  width: 150px;
  height: 150px;
  background: var(--gradient-alt);
  border-radius: 30px;
  z-index: -1;
  opacity: 0.5;
}

.section-subtitle {
  font-size: 0.95rem;
  font-weight: 600;
  letter-spacing: 3px;
  text-transform: uppercase;
  color: #667eea;
  margin-bottom: 1rem;
}

.dark-mode .section-subtitle {
  color: #8b9aff;
}

.section-title {
  margin-bottom: 1.5rem;
  color: var(--text-dark);
}

.about-text {
  margin-bottom: 1.5rem;
  font-size: 1.0625rem;
  line-height: 1.8;
}

.skills {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 1.5rem;
  margin: 3rem 0;
}

.skill-item {
  padding: 1.5rem;
  background: white;
  border-radius: 15px;
  transition: all 0.3s ease;
  border: 2px solid transparent;
}

.dark-mode .skill-item {
  background: #1a1a1a;
  border-color: #2a2a2a;
}

.skill-item:hover {
  border-color: #667eea;
  transform: translateY(-5px);
  box-shadow: 0 10px 30px rgba(102, 126, 234, 0.15);
}

.dark-mode .skill-item:hover {
  box-shadow: 0 10px 30px rgba(102, 126, 234, 0.3);
}

.skill-icon {
  font-size: 2.5rem;
  margin-bottom: 1rem;
}

.skill-item h4 {
  font-size: 1.125rem;
  margin-bottom: 0.5rem;
  color: var(--text-dark);
}

.skill-item p {
  font-size: 0.95rem;
  color: var(--text-light);
  line-height: 1.6;
}

/* Responsive */
@media (max-width: 1024px) {
  .about-grid {
    gap: 4rem;
  }

  .skills {
    grid-template-columns: 1fr;
  }
}

@media (max-width: 768px) {
  .about {
    padding: 5rem 0;
  }

  .about-grid {
    grid-template-columns: 1fr;
    gap: 3rem;
  }

  .decorative-element {
    width: 100px;
    height: 100px;
    top: -15px;
    right: -15px;
  }

  .skills {
    gap: 1rem;
  }

  .skill-item {
    padding: 1.25rem;
  }

  .skill-icon {
    font-size: 2rem;
  }
}

@media (max-width: 480px) {
  .about {
    padding: 4rem 0;
  }

  .skill-item {
    padding: 1rem;
  }

  .skill-item h4 {
    font-size: 1rem;
  }

  .skill-item p {
    font-size: 0.9rem;
  }
}
</style>
