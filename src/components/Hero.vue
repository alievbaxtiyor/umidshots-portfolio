<template>
  <section id="home" class="hero">
    <div class="hero-background">
      <div class="gradient-blob blob-1"></div>
      <div class="gradient-blob blob-2"></div>
      <div class="gradient-blob blob-3"></div>
    </div>

    <div class="container hero-container">
      <div class="hero-content">
        <p class="hero-subtitle fade-in-up">{{ translations.hero.subtitle }}</p>
        <h1 class="hero-title fade-in-up">
          {{ translations.hero.title1 }}<br />
          {{ translations.hero.title2 }} <span class="gradient-text">{{ translations.hero.title3 }}</span>
        </h1>
        <p class="hero-description fade-in-up">
          {{ translations.hero.description }}
        </p>
        <div class="hero-buttons fade-in-up">
          <a href="#portfolio" class="btn btn-primary">{{ translations.hero.viewWork }}</a>
          <a href="#contact" class="btn btn-outline">{{ translations.hero.getInTouch }}</a>
        </div>

        <div class="hero-stats fade-in">
          <div class="stat">
            <h3>500+</h3>
            <p>{{ translations.hero.projects }}</p>
          </div>
          <div class="stat">
            <h3>50K+</h3>
            <p>{{ translations.hero.followers }}</p>
          </div>
          <div class="stat">
            <h3>3+</h3>
            <p>{{ translations.hero.years }}</p>
          </div>
        </div>
      </div>

      <div class="hero-visual fade-in">
        <div class="visual-card card-1">
          <div class="card-shimmer"></div>
        </div>
        <div class="visual-card card-2">
          <div class="card-shimmer"></div>
        </div>
        <div class="visual-card card-3">
          <div class="card-shimmer"></div>
        </div>
      </div>
    </div>

    <div class="scroll-indicator">
      <div class="mouse">
        <div class="wheel"></div>
      </div>
      <p>{{ translations.hero.scrollDown }}</p>
    </div>
  </section>
</template>

<script>
export default {
  name: 'Hero',
  props: {
    translations: {
      type: Object,
      required: true
    }
  }
}
</script>

<style scoped>
.hero {
  position: relative;
  min-height: 100vh;
  display: flex;
  align-items: center;
  padding: 8rem 0 6rem;
  overflow: hidden;
}

.hero-background {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  z-index: -1;
  overflow: hidden;
}

.gradient-blob {
  position: absolute;
  border-radius: 50%;
  filter: blur(80px);
  opacity: 0.3;
  animation: float 20s infinite ease-in-out;
}

.blob-1 {
  width: 500px;
  height: 500px;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  top: -10%;
  right: -10%;
  animation-delay: 0s;
}

.blob-2 {
  width: 400px;
  height: 400px;
  background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
  bottom: -10%;
  left: -5%;
  animation-delay: -7s;
}

.blob-3 {
  width: 300px;
  height: 300px;
  background: linear-gradient(135deg, #4facfe 0%, #00f2fe 100%);
  top: 40%;
  left: 40%;
  animation-delay: -14s;
}

@keyframes float {
  0%, 100% {
    transform: translate(0, 0) scale(1);
  }
  33% {
    transform: translate(50px, -50px) scale(1.1);
  }
  66% {
    transform: translate(-50px, 50px) scale(0.9);
  }
}

.hero-container {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 4rem;
  align-items: center;
}

.hero-content {
  z-index: 1;
}

.hero-subtitle {
  font-size: 1rem;
  font-weight: 600;
  letter-spacing: 3px;
  text-transform: uppercase;
  color: #667eea;
  margin-bottom: 1rem;
  animation-delay: 0.2s;
}

.dark-mode .hero-subtitle {
  color: #8b9aff;
}

.hero-title {
  margin-bottom: 1.5rem;
  animation-delay: 0.4s;
}

.gradient-text {
  background: var(--gradient);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.hero-description {
  font-size: 1.125rem;
  line-height: 1.8;
  margin-bottom: 2.5rem;
  max-width: 550px;
  animation-delay: 0.6s;
}

.hero-buttons {
  display: flex;
  gap: 1.5rem;
  flex-wrap: wrap;
  animation-delay: 0.8s;
}

.hero-stats {
  display: flex;
  gap: 3rem;
  margin-top: 4rem;
  animation-delay: 1s;
}

.stat h3 {
  font-size: 2.5rem;
  font-weight: 800;
  background: var(--gradient);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  margin-bottom: 0.25rem;
}

.stat p {
  font-size: 0.95rem;
  color: var(--text-light);
}

.hero-visual {
  position: relative;
  height: 600px;
  display: flex;
  justify-content: center;
  align-items: center;
  animation-delay: 1.2s;
}

.visual-card {
  position: absolute;
  width: 280px;
  height: 400px;
  border-radius: 20px;
  background: linear-gradient(135deg, #f5f5f5 0%, #e0e0e0 100%);
  box-shadow: 0 20px 60px rgba(0, 0, 0, 0.1);
  overflow: hidden;
  transition: transform 0.3s ease;
}

.dark-mode .visual-card {
  background: linear-gradient(135deg, #2a2a2a 0%, #1a1a1a 100%);
  box-shadow: 0 20px 60px rgba(0, 0, 0, 0.5);
}

.visual-card:hover {
  transform: translateY(-10px);
}

.card-1 {
  z-index: 3;
  transform: rotate(-5deg);
}

.card-2 {
  z-index: 2;
  transform: rotate(5deg) translateX(-50px);
  opacity: 0.8;
}

.card-3 {
  z-index: 1;
  transform: rotate(-3deg) translateX(50px);
  opacity: 0.6;
}

.card-shimmer {
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(90deg,
    transparent,
    rgba(255, 255, 255, 0.3),
    transparent
  );
  animation: shimmer 3s infinite;
}

@keyframes shimmer {
  0% {
    left: -100%;
  }
  100% {
    left: 100%;
  }
}

.scroll-indicator {
  position: absolute;
  bottom: 3rem;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.5rem;
  opacity: 0.6;
  animation: fadeIn 1s ease 1.5s forwards, bounce 2s infinite 2s;
}

.mouse {
  width: 30px;
  height: 50px;
  border: 2px solid var(--text-dark);
  border-radius: 15px;
  display: flex;
  justify-content: center;
  padding-top: 8px;
}

.dark-mode .mouse {
  border-color: var(--text-light);
}

.wheel {
  width: 4px;
  height: 10px;
  background: var(--text-dark);
  border-radius: 2px;
  animation: scroll 1.5s infinite;
}

.dark-mode .wheel {
  background: var(--text-light);
}

@keyframes scroll {
  0% {
    opacity: 1;
    transform: translateY(0);
  }
  100% {
    opacity: 0;
    transform: translateY(15px);
  }
}

@keyframes bounce {
  0%, 100% {
    transform: translateX(-50%) translateY(0);
  }
  50% {
    transform: translateX(-50%) translateY(-10px);
  }
}

.scroll-indicator p {
  font-size: 0.75rem;
  text-transform: uppercase;
  letter-spacing: 2px;
  font-weight: 600;
}

/* Responsive */
@media (max-width: 1024px) {
  .hero-container {
    grid-template-columns: 1fr;
    gap: 3rem;
  }

  .hero-visual {
    height: 400px;
  }

  .visual-card {
    width: 220px;
    height: 320px;
  }
}

@media (max-width: 768px) {
  .hero {
    padding: 7rem 0 4rem;
  }

  .hero-buttons {
    flex-direction: column;
    align-items: flex-start;
  }

  .hero-buttons .btn {
    width: 100%;
    text-align: center;
  }

  .hero-stats {
    gap: 2rem;
  }

  .stat h3 {
    font-size: 2rem;
  }

  .hero-visual {
    height: 300px;
  }

  .visual-card {
    width: 180px;
    height: 260px;
  }

  .scroll-indicator {
    bottom: 2rem;
  }
}

@media (max-width: 480px) {
  .hero-stats {
    gap: 1.5rem;
  }

  .stat h3 {
    font-size: 1.75rem;
  }

  .stat p {
    font-size: 0.85rem;
  }
}
</style>
