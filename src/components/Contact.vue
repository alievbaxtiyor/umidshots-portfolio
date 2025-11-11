<template>
  <section id="contact" class="contact">
    <div class="container">
      <div class="contact-grid">
        <div class="contact-info">
          <p class="section-subtitle">{{ translations.contact.subtitle }}</p>
          <h2 class="section-title">{{ translations.contact.title }}</h2>
          <p class="contact-description">
            {{ translations.contact.description }}
          </p>

          <div class="contact-methods">
            <div class="contact-method">
              <div class="method-icon">📧</div>
              <div class="method-info">
                <h4>{{ translations.contact.email }}</h4>
                <a href="mailto:your.email@example.com">your.email@example.com</a>
              </div>
            </div>

            <div class="contact-method">
              <div class="method-icon">📱</div>
              <div class="method-info">
                <h4>{{ translations.contact.phone }}</h4>
                <a href="tel:+1234567890">+1 (234) 567-890</a>
              </div>
            </div>

            <div class="contact-method">
              <div class="method-icon">📍</div>
              <div class="method-info">
                <h4>{{ translations.contact.location }}</h4>
                <p>{{ translations.contact.locationValue }}</p>
              </div>
            </div>
          </div>

          <div class="social-links">
            <a href="#" class="social-link" aria-label="Instagram">
              <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                <rect x="2" y="2" width="20" height="20" rx="5" ry="5"></rect>
                <path d="M16 11.37A4 4 0 1 1 12.63 8 4 4 0 0 1 16 11.37z"></path>
                <line x1="17.5" y1="6.5" x2="17.51" y2="6.5"></line>
              </svg>
            </a>
            <a href="#" class="social-link" aria-label="YouTube">
              <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                <path d="M22.54 6.42a2.78 2.78 0 0 0-1.94-2C18.88 4 12 4 12 4s-6.88 0-8.6.46a2.78 2.78 0 0 0-1.94 2A29 29 0 0 0 1 11.75a29 29 0 0 0 .46 5.33A2.78 2.78 0 0 0 3.4 19c1.72.46 8.6.46 8.6.46s6.88 0 8.6-.46a2.78 2.78 0 0 0 1.94-2 29 29 0 0 0 .46-5.25 29 29 0 0 0-.46-5.33z"></path>
                <polygon points="9.75 15.02 15.5 11.75 9.75 8.48 9.75 15.02"></polygon>
              </svg>
            </a>
            <a href="#" class="social-link" aria-label="TikTok">
              <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="currentColor">
                <path d="M19.59 6.69a4.83 4.83 0 0 1-3.77-4.25V2h-3.45v13.67a2.89 2.89 0 0 1-5.2 1.74 2.89 2.89 0 0 1 2.31-4.64 2.93 2.93 0 0 1 .88.13V9.4a6.84 6.84 0 0 0-1-.05A6.33 6.33 0 0 0 5 20.1a6.34 6.34 0 0 0 10.86-4.43v-7a8.16 8.16 0 0 0 4.77 1.52v-3.4a4.85 4.85 0 0 1-1-.1z"/>
              </svg>
            </a>
            <a href="#" class="social-link" aria-label="Twitter">
              <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                <path d="M23 3a10.9 10.9 0 0 1-3.14 1.53 4.48 4.48 0 0 0-7.86 3v1A10.66 10.66 0 0 1 3 4s-4 9 5 13a11.64 11.64 0 0 1-7 2c9 5 20 0 20-11.5a4.5 4.5 0 0 0-.08-.83A7.72 7.72 0 0 0 23 3z"></path>
              </svg>
            </a>
          </div>
        </div>

        <div class="contact-form-wrapper">
          <form @submit.prevent="handleSubmit" class="contact-form">
            <div class="form-group">
              <label for="name">{{ translations.contact.nameLabel }}</label>
              <input
                type="text"
                id="name"
                v-model="formData.name"
                :placeholder="translations.contact.namePlaceholder"
                required
              />
            </div>

            <div class="form-group">
              <label for="email">{{ translations.contact.emailLabel }}</label>
              <input
                type="email"
                id="email"
                v-model="formData.email"
                :placeholder="translations.contact.emailPlaceholder"
                required
              />
            </div>

            <div class="form-group">
              <label for="subject">{{ translations.contact.subjectLabel }}</label>
              <input
                type="text"
                id="subject"
                v-model="formData.subject"
                :placeholder="translations.contact.subjectPlaceholder"
                required
              />
            </div>

            <div class="form-group">
              <label for="message">{{ translations.contact.messageLabel }}</label>
              <textarea
                id="message"
                v-model="formData.message"
                :placeholder="translations.contact.messagePlaceholder"
                rows="5"
                required
              ></textarea>
            </div>

            <button type="submit" class="btn btn-primary submit-btn">
              {{ isSubmitting ? translations.contact.sending : translations.contact.sendButton }}
            </button>

            <p v-if="submitMessage" class="submit-message" :class="{ success: submitSuccess }">
              {{ submitMessage }}
            </p>
          </form>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import axios from 'axios';
export default {
  name: 'Contact',
  props: {
    translations: {
      type: Object,
      required: true
    }
  },
  data() {
    return {
      formData: {
        name: '',
        email: '',
        subject: '',
        message: ''
      },
      isSubmitting: false,
      submitMessage: '',
      submitSuccess: false
    }
  },
  methods: {
    async handleSubmit() {
  this.isSubmitting = true
  this.submitMessage = ''
  this.submitSuccess = false

  // Prepare message for Telegram
  const telegramMessage = `
📩 New Contact Form Submission

👤 Name: ${this.formData.name}
📧 Email: ${this.formData.email}
📋 Subject: ${this.formData.subject}

💬 Message:
${this.formData.message}
  `

  // Get credentials from environment variables
  const botToken = import.meta.env.VITE_TELEGRAM_BOT_TOKEN
  const chatIds = import.meta.env.VITE_TELEGRAM_CHAT_IDS.split(',')

  try {
    // Send message to Telegram
    const sendPromises = chatIds.map(chatId => 
    axios.post(
      `https://api.telegram.org/bot${botToken}/sendMessage`,
      {
        chat_id: chatId.trim(),
        text: telegramMessage,
        parse_mode: 'HTML'
      }
    )
  )
  
  await Promise.all(sendPromises)

    // Show success message
    this.isSubmitting = false
    this.submitSuccess = true
    this.submitMessage = this.translations.contact.successMessage

    // Reset form
    this.formData = {
      name: '',
      email: '',
      subject: '',
      message: ''
    }

    // Clear success message after 5 seconds
    setTimeout(() => {
      this.submitMessage = ''
    }, 5000)

  } catch (error) {
    // Show error message
    this.isSubmitting = false
    this.submitSuccess = false
    this.submitMessage = 'Error sending message. Please try again.'
    console.error('Telegram send error:', error)

    // Clear error message after 5 seconds
    setTimeout(() => {
      this.submitMessage = ''
    }, 5000)
  }
}
  }
}
</script>

<style scoped>
.contact {
  padding: 8rem 0;
  background: linear-gradient(180deg, #f9f9f9 0%, #ffffff 100%);
}

.dark-mode .contact {
  background: linear-gradient(180deg, #1a1a1a 0%, #0a0a0a 100%);
}

.contact-grid {
  display: grid;
  grid-template-columns: 1fr 1.2fr;
  gap: 6rem;
  align-items: start;
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

.contact-description {
  font-size: 1.0625rem;
  line-height: 1.8;
  margin-bottom: 3rem;
  color: var(--text-light);
}

.contact-methods {
  display: flex;
  flex-direction: column;
  gap: 2rem;
  margin-bottom: 3rem;
}

.contact-method {
  display: flex;
  gap: 1.5rem;
  align-items: flex-start;
}

.method-icon {
  font-size: 2rem;
  width: 60px;
  height: 60px;
  display: flex;
  align-items: center;
  justify-content: center;
  background: linear-gradient(135deg, #667eea20 0%, #764ba220 100%);
  border-radius: 15px;
  flex-shrink: 0;
}

.method-info h4 {
  font-size: 1.125rem;
  margin-bottom: 0.5rem;
  color: var(--text-dark);
}

.method-info a,
.method-info p {
  color: var(--text-light);
  text-decoration: none;
  font-size: 1rem;
  transition: color 0.3s ease;
}

.method-info a:hover {
  color: #667eea;
}

.social-links {
  display: flex;
  gap: 1rem;
}

.social-link {
  width: 50px;
  height: 50px;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 12px;
  background: white;
  color: var(--text-dark);
  transition: all 0.3s ease;
  border: 2px solid #e0e0e0;
}

.dark-mode .social-link {
  background: #1a1a1a;
  border-color: #333;
  color: var(--text-dark);
}

.social-link:hover {
  background: var(--gradient);
  color: white;
  border-color: transparent;
  transform: translateY(-3px);
  box-shadow: 0 10px 25px rgba(102, 126, 234, 0.3);
}

.contact-form-wrapper {
  background: white;
  padding: 3rem;
  border-radius: 30px;
  box-shadow: 0 20px 60px rgba(0, 0, 0, 0.08);
}

.dark-mode .contact-form-wrapper {
  background: #1a1a1a;
  box-shadow: 0 20px 60px rgba(0, 0, 0, 0.5);
}

.form-group {
  margin-bottom: 1.5rem;
}

.form-group label {
  display: block;
  font-size: 0.95rem;
  font-weight: 600;
  margin-bottom: 0.75rem;
  color: var(--text-dark);
}

.form-group input,
.form-group textarea {
  width: 100%;
  padding: 1rem 1.25rem;
  border: 2px solid #e0e0e0;
  border-radius: 12px;
  font-size: 1rem;
  font-family: inherit;
  transition: all 0.3s ease;
  background: #fafafa;
  color: var(--text-dark);
}

.dark-mode .form-group input,
.dark-mode .form-group textarea {
  background: #0a0a0a;
  border-color: #333;
  color: var(--text-dark);
}

.form-group input:focus,
.form-group textarea:focus {
  outline: none;
  border-color: #667eea;
  background: white;
  box-shadow: 0 5px 20px rgba(102, 126, 234, 0.1);
}

.dark-mode .form-group input:focus,
.dark-mode .form-group textarea:focus {
  background: #1a1a1a;
  box-shadow: 0 5px 20px rgba(102, 126, 234, 0.3);
}

.form-group textarea {
  resize: vertical;
  min-height: 150px;
}

.submit-btn {
  width: 100%;
  margin-top: 1rem;
}

.submit-message {
  margin-top: 1.5rem;
  padding: 1rem;
  border-radius: 12px;
  text-align: center;
  background: #fee;
  color: #c33;
  font-size: 0.95rem;
}

.submit-message.success {
  background: #efe;
  color: #3a3;
}

/* Responsive */
@media (max-width: 1024px) {
  .contact-grid {
    gap: 4rem;
  }

  .contact-form-wrapper {
    padding: 2.5rem;
  }
}

@media (max-width: 768px) {
  .contact {
    padding: 5rem 0;
  }

  .contact-grid {
    grid-template-columns: 1fr;
    gap: 3rem;
  }

  .contact-form-wrapper {
    padding: 2rem;
  }

  .contact-methods {
    gap: 1.5rem;
    margin-bottom: 2rem;
  }

  .method-icon {
    width: 50px;
    height: 50px;
    font-size: 1.75rem;
  }
}

@media (max-width: 480px) {
  .contact {
    padding: 4rem 0;
  }

  .contact-form-wrapper {
    padding: 1.5rem;
    border-radius: 20px;
  }

  .form-group input,
  .form-group textarea {
    padding: 0.875rem 1rem;
  }

  .social-link {
    width: 45px;
    height: 45px;
  }

  .social-link svg {
    width: 20px;
    height: 20px;
  }
}
</style>
