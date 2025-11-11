<template>
  <section id="portfolio" class="portfolio">
    <div class="container">
      <div class="section-header">
        <p class="section-subtitle">{{ translations.portfolio.subtitle }}</p>
        <h2 class="section-title">{{ translations.portfolio.title }}</h2>
        <p class="section-description">
          {{ translations.portfolio.description }}
        </p>
      </div>

      <div class="filter-buttons">
        <button
          v-for="category in categories"
          :key="category.key"
          @click="filterProjects(category.key)"
          :class="{ active: activeCategory === category.key }"
          class="filter-btn"
        >
          {{ category.label }}
        </button>
      </div>

      <div class="portfolio-grid">
        <div
          v-for="project in filteredProjects"
          :key="project.id"
          class="portfolio-item"
          :style="{ animationDelay: project.id * 0.1 + 's' }"
        >
          <div class="portfolio-card">
            <div class="card-image">
              <div class="image-placeholder">
                <span class="placeholder-icon">{{ project.icon }}</span>
              </div>
              <div class="card-overlay">
                <div class="overlay-content">
                  <h3>{{ project.title }}</h3>
                  <p>{{ project.description }}</p>
                  <span class="category-tag">{{ project.category }}</span>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>

      <div class="cta-section">
        <h3>{{ translations.portfolio.ctaTitle }}</h3>
        <p>{{ translations.portfolio.ctaText }}</p>
        <a href="#contact" class="btn btn-primary">{{ translations.portfolio.ctaButton }}</a>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'Portfolio',
  props: {
    translations: {
      type: Object,
      required: true
    }
  },
  data() {
    return {
      activeCategory: 'All'
    }
  },
  computed: {
    categories() {
      return [
        { key: 'All', label: this.translations.portfolio.all },
        { key: 'Photography', label: this.translations.portfolio.photography },
        { key: 'Video', label: this.translations.portfolio.video },
        { key: 'Commercial', label: this.translations.portfolio.commercial },
        { key: 'Portrait', label: this.translations.portfolio.portrait }
      ]
    },
    projects() {
      return [
        {
          id: 1,
          title: this.translations.portfolio.projects.urbanSunset.title,
          description: this.translations.portfolio.projects.urbanSunset.description,
          category: 'Photography',
          icon: '🌆'
        },
        {
          id: 2,
          title: this.translations.portfolio.projects.brandCampaign.title,
          description: this.translations.portfolio.projects.brandCampaign.description,
          category: 'Commercial',
          icon: '📱'
        },
        {
          id: 3,
          title: this.translations.portfolio.projects.streetStories.title,
          description: this.translations.portfolio.projects.streetStories.description,
          category: 'Video',
          icon: '🎬'
        },
        {
          id: 4,
          title: this.translations.portfolio.projects.portraitSeries.title,
          description: this.translations.portfolio.projects.portraitSeries.description,
          category: 'Portrait',
          icon: '👤'
        },
        {
          id: 5,
          title: this.translations.portfolio.projects.natureMoments.title,
          description: this.translations.portfolio.projects.natureMoments.description,
          category: 'Photography',
          icon: '🌿'
        },
        {
          id: 6,
          title: this.translations.portfolio.projects.productShots.title,
          description: this.translations.portfolio.projects.productShots.description,
          category: 'Commercial',
          icon: '📦'
        },
        {
          id: 7,
          title: this.translations.portfolio.projects.nightLights.title,
          description: this.translations.portfolio.projects.nightLights.description,
          category: 'Photography',
          icon: '🌃'
        },
        {
          id: 8,
          title: this.translations.portfolio.projects.travelVlog.title,
          description: this.translations.portfolio.projects.travelVlog.description,
          category: 'Video',
          icon: '✈️'
        },
        {
          id: 9,
          title: this.translations.portfolio.projects.creativePortraits.title,
          description: this.translations.portfolio.projects.creativePortraits.description,
          category: 'Portrait',
          icon: '🎭'
        }
      ]
    },
    filteredProjects() {
      if (this.activeCategory === 'All') {
        return this.projects
      }
      return this.projects.filter(p => p.category === this.activeCategory)
    }
  },
  methods: {
    filterProjects(category) {
      this.activeCategory = category
    }
  }
}
</script>

<style scoped>
.portfolio {
  padding: 8rem 0;
  background: white;
}

.dark-mode .portfolio {
  background: #0a0a0a;
}

.section-header {
  text-align: center;
  max-width: 700px;
  margin: 0 auto 4rem;
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
  margin-bottom: 1rem;
  color: var(--text-dark);
}

.section-description {
  font-size: 1.125rem;
  color: var(--text-light);
}

.filter-buttons {
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  gap: 1rem;
  margin-bottom: 4rem;
}

.filter-btn {
  padding: 0.75rem 2rem;
  background: white;
  border: 2px solid #e0e0e0;
  border-radius: 50px;
  font-size: 0.95rem;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.3s ease;
  color: var(--text-dark);
}

.dark-mode .filter-btn {
  background: #1a1a1a;
  border-color: #333;
  color: var(--text-dark);
}

.filter-btn:hover {
  border-color: #667eea;
  color: #667eea;
  transform: translateY(-2px);
}

.filter-btn.active {
  background: var(--gradient);
  border-color: transparent;
  color: white;
  box-shadow: 0 5px 20px rgba(102, 126, 234, 0.3);
}

.portfolio-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(350px, 1fr));
  gap: 2rem;
  margin-bottom: 5rem;
}

.portfolio-item {
  animation: fadeInUp 0.6s ease forwards;
  opacity: 0;
}

.portfolio-card {
  border-radius: 20px;
  overflow: hidden;
  height: 100%;
  transition: transform 0.3s ease;
}

.portfolio-card:hover {
  transform: translateY(-10px);
}

.card-image {
  position: relative;
  aspect-ratio: 4/5;
  overflow: hidden;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
}

.image-placeholder {
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  background: linear-gradient(135deg,
    rgba(102, 126, 234, 0.9) 0%,
    rgba(118, 75, 162, 0.9) 100%
  );
}

.placeholder-icon {
  font-size: 5rem;
  filter: grayscale(100%) brightness(1.5);
}

.card-overlay {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: linear-gradient(
    to top,
    rgba(0, 0, 0, 0.9) 0%,
    rgba(0, 0, 0, 0.6) 50%,
    rgba(0, 0, 0, 0.2) 100%
  );
  display: flex;
  align-items: flex-end;
  padding: 2rem;
  opacity: 0;
  transition: opacity 0.3s ease;
}

.portfolio-card:hover .card-overlay {
  opacity: 1;
}

.overlay-content {
  color: white;
}

.overlay-content h3 {
  font-size: 1.5rem;
  margin-bottom: 0.5rem;
  color: white;
}

.overlay-content p {
  font-size: 1rem;
  margin-bottom: 1rem;
  color: rgba(255, 255, 255, 0.9);
}

.category-tag {
  display: inline-block;
  padding: 0.4rem 1rem;
  background: rgba(255, 255, 255, 0.2);
  backdrop-filter: blur(10px);
  border-radius: 20px;
  font-size: 0.85rem;
  font-weight: 600;
  color: white;
  border: 1px solid rgba(255, 255, 255, 0.3);
}

.cta-section {
  text-align: center;
  padding: 4rem 2rem;
  background: linear-gradient(135deg, #f8f9ff 0%, #f0f2ff 100%);
  border-radius: 30px;
}

.dark-mode .cta-section {
  background: linear-gradient(135deg, #1a1a2e 0%, #16213e 100%);
}

.cta-section h3 {
  font-size: 2rem;
  margin-bottom: 1rem;
  color: var(--text-dark);
}

.cta-section p {
  font-size: 1.125rem;
  color: var(--text-light);
  margin-bottom: 2rem;
}

/* Responsive */
@media (max-width: 1024px) {
  .portfolio-grid {
    grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  }
}

@media (max-width: 768px) {
  .portfolio {
    padding: 5rem 0;
  }

  .section-header {
    margin-bottom: 3rem;
  }

  .filter-buttons {
    margin-bottom: 3rem;
  }

  .portfolio-grid {
    grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
    gap: 1.5rem;
    margin-bottom: 4rem;
  }

  .card-overlay {
    opacity: 1;
  }

  .cta-section {
    padding: 3rem 1.5rem;
  }

  .cta-section h3 {
    font-size: 1.75rem;
  }
}

@media (max-width: 480px) {
  .portfolio {
    padding: 4rem 0;
  }

  .filter-buttons {
    gap: 0.75rem;
  }

  .filter-btn {
    padding: 0.625rem 1.5rem;
    font-size: 0.875rem;
  }

  .portfolio-grid {
    grid-template-columns: 1fr;
    gap: 1.25rem;
  }

  .overlay-content h3 {
    font-size: 1.25rem;
  }

  .overlay-content p {
    font-size: 0.95rem;
  }

  .cta-section h3 {
    font-size: 1.5rem;
  }

  .cta-section p {
    font-size: 1rem;
  }
}
</style>
