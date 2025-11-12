<template>
  <section id="writeMe" class="write-me-section">
    <div class="container">
      <!-- Section Title - Matching Projects section exactly -->
      <div class="section-header">
        <p class="section-subtitle">Get in touch with</p>
        <h1 class="section-title">Write Me</h1>
      </div>

      <div class="content-grid">
        <!-- Left side - Simple mail icon -->
        <div class="icon-side">
          <div class="mail-icon-container">
            <div class="mail-icon">
              <!-- Email Icon -->
              <svg xmlns="http://www.w3.org/2000/svg" x="0px" y="0px" width="100" height="100" viewBox="0 0 48 48">
                <path fill="#4caf50" d="M45,16.2l-5,2.75l-5,4.75L35,40h7c1.657,0,3-1.343,3-3V16.2z"></path>
                <path fill="#1e88e5" d="M3,16.2l3.614,1.71L13,23.7V40H6c-1.657,0-3-1.343-3-3V16.2z"></path>
                <polygon fill="#e53935" points="35,11.2 24,19.45 13,11.2 12,17 13,23.7 24,31.95 35,23.7 36,17"></polygon>
                <path fill="#c62828" d="M3,12.298V16.2l10,7.5V11.2L9.876,8.859C9.132,8.301,8.228,8,7.298,8h0C4.924,8,3,9.924,3,12.298z"></path>
                <path fill="#fbc02d" d="M45,12.298V16.2l-10,7.5V11.2l3.124-2.341C38.868,8.301,39.772,8,40.702,8h0 C43.076,8,45,9.924,45,12.298z"></path>
              </svg>
            </div>
            <h3 class="icon-text">Get In Touch</h3>
            <p class="icon-description">Send me a message and I'll get back to you soon!</p>
          </div>
        </div>

        <!-- Right side - Dark mode form -->
        <div class="form-side">
          <form @submit.prevent="sendEmail" class="contact-form">
            <div class="form-group">
              <label for="clientEmail" class="form-label">Your Email</label>
              <input 
                id="clientEmail"
                type="email" 
                v-model="clientEmail" 
                required
                class="form-input"
                placeholder="Enter your email"
              >
            </div>

            <div class="form-group">
              <label for="subject" class="form-label">Subject</label>
              <input 
                id="subject"
                type="text" 
                v-model="subject" 
                required
                class="form-input"
                placeholder="What's this about?"
              >
            </div>
            
            <div class="form-group full-width">
              <label for="message" class="form-label">Message</label>
              <textarea 
                id="message"
                v-model="message" 
                placeholder="Write your message here..."
                rows="3"
                required
                class="form-textarea"
              ></textarea>
            </div>
            
            <button type="submit" class="submit-button">
              <span>Send Message</span>
              <svg width="20" height="20" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                <line x1="22" y1="2" x2="11" y2="13" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                <polygon points="22,2 15,22 11,13 2,9 22,2" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
              </svg>
            </button>
          </form>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: "WriteMe",
  data() {
    return {
      clientEmail: "",
      subject: "",
      message: ""
    };
  },
  methods: {
    sendEmail() {
      if (this.clientEmail.trim() && this.subject.trim() && this.message.trim()) {
        // Create email body with client details
        const emailBody = `From: ${this.clientEmail}\n\nSubject: ${this.subject}\n\nMessage:\n${this.message}\n\n---\nSent from Portfolio Contact Form`;
        
        // Send email to your address with client's information
        const mailtoLink = `mailto:radhakrishna02256@gmail.com?subject=${encodeURIComponent(`Portfolio Contact: ${this.subject}`)}&body=${encodeURIComponent(emailBody)}`;
        
        window.location.href = mailtoLink;
        
        // Optional: Clear form after sending
        this.clientEmail = "";
        this.subject = "";
        this.message = "";
      }
    }
  }
};
</script>

<style scoped>
.write-me-section {
  padding: 80px 0;
  background: #000000;
  min-height: 100vh;
  scroll-snap-align: start;
  position: relative;
  z-index: 1;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 20px;
  width: 100%;
}

/* Section Header - Exactly matching Projects section heading style */
.section-header {
  text-align: center;
  margin-top: 30px;
  margin-bottom: 80px;
}

.section-title {
  font-family: 'Orbitron', 'Helvetica', sans-serif;
  font-weight: bold;
  color: white !important;
  text-shadow: 3px 3px 6px rgba(0, 0, 0, 0.8);
  font-size: 2.5rem;
  letter-spacing: 2px;
  text-transform: uppercase;
  background: linear-gradient(45deg, #ffffff, #e0e0e0);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  position: relative;
  margin-bottom: 20px;
}

.section-title::after {
  content: '';
  position: absolute;
  bottom: -10px;
  left: 50%;
  transform: translateX(-50%);
  width: 80px;
  height: 3px;
  background: linear-gradient(45deg, rgba(255, 255, 255, 0.8), rgba(255, 255, 255, 0.4));
  border-radius: 2px;
}

.section-subtitle {
  color: rgba(255, 255, 255, 0.8) !important;
  text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.8);
  font-size: 1.2rem;
  letter-spacing: 1px;
  text-transform: uppercase;
  font-weight: 300;
  margin-bottom: 16px;
}

.section-underline {
  width: 80px;
  height: 4px;
  background: linear-gradient(135deg, #666666 0%, #333333 100%);
  margin: 0 auto;
  border-radius: 2px;
}

.content-grid {
  display: grid;
  grid-template-columns: 1fr 2fr;
  gap: 60px;
  align-items: start;
  max-width: 1400px;
  margin: 0 auto;
}

/* Left side - Simple mail icon */
.icon-side {
  display: flex;
  justify-content: center;
  align-items: flex-start;
  padding-top: 40px;
}

.mail-icon-container {
  text-align: center;
  padding: 20px;
}

.mail-icon {
  width: 120px;
  height: 120px;
  margin: 0 auto 20px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.icon-text {
  font-size: 1.5rem;
  font-weight: 600;
  color: #e2e8f0;
  margin-bottom: 12px;
}

.icon-description {
  font-size: 1rem;
  color: #94a3b8;
  line-height: 1.6;
}

/* Right side - True black theme form */
.form-side {
  background: #000000;
  padding: 30px 40px;
  border-radius: 12px;
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.25);
  border: 1px solid #333333;
  width: 100%;
  max-width: 700px;
}

.contact-form {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 16px;
}

.form-group {
  display: flex;
  flex-direction: column;
  gap: 5px;
}

.form-group.full-width {
  grid-column: 1 / -1;
}

.form-label {
  font-size: 0.8rem;
  font-weight: 600;
  color: #e2e8f0;
  text-transform: uppercase;
  letter-spacing: 0.5px;
}

.form-input,
.form-textarea {
  padding: 12px 16px;
  border: 2px solid #333333;
  border-radius: 8px;
  font-size: 0.9rem;
  background: #000000;
  transition: all 0.3s ease;
  color: #e2e8f0;
  font-family: inherit;
}

.form-input::placeholder,
.form-textarea::placeholder {
  color: #94a3b8;
}

.form-input:focus,
.form-textarea:focus {
  outline: none;
  border-color: #666666;
  background: #111111;
  box-shadow: 0 0 0 3px rgba(102, 102, 102, 0.1);
}

.form-textarea {
  resize: vertical;
  min-height: 80px;
  line-height: 1.4;
}

.submit-button {
  background: linear-gradient(135deg, #64748b 0%, #475569 100%);
  color: white;
  border: none;
  padding: 12px 24px;
  border-radius: 8px;
  font-size: 0.95rem;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.3s ease;
  text-transform: uppercase;
  letter-spacing: 0.5px;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 6px;
  grid-column: 1 / -1;
  margin-top: 8px;
  max-width: 180px;
  justify-self: center;
}

.submit-button:hover {
  transform: translateY(-2px);
  box-shadow: 0 15px 35px rgba(100, 116, 139, 0.4);
  background: linear-gradient(135deg, #475569 0%, #334155 100%);
}

.submit-button:active {
  transform: translateY(0);
}

/* Responsive Design */
@media (max-width: 768px) {
  .write-me-section {
    padding: 60px 0;
  }

  .section-header {
    margin-bottom: 60px;
  }

  .section-title {
    font-size: 2rem;
  }

  .section-subtitle {
    font-size: 1rem;
  }

  .content-grid {
    grid-template-columns: 1fr;
    gap: 30px;
    padding: 0 10px;
  }
  
  .mail-icon-container {
    padding: 15px;
  }

  .mail-icon {
    width: 70px;
    height: 70px;
  }

  .icon-text {
    font-size: 1.25rem;
  }
  
  .form-side {
    padding: 25px 20px;
    max-width: 100%;
  }

  .contact-form {
    grid-template-columns: 1fr;
    gap: 16px;
  }

  .form-input,
  .form-textarea {
    padding: 12px 16px;
  }

  .submit-button {
    padding: 12px 24px;
    font-size: 0.9rem;
  }
}

@media (max-width: 480px) {
  .section-title {
    font-size: 1.8rem;
  }

  .mail-icon {
    width: 60px;
    height: 60px;
  }

  .icon-text {
    font-size: 1.1rem;
  }

  .form-side {
    padding: 20px 15px;
  }

  .form-input,
  .form-textarea {
    padding: 10px 14px;
    font-size: 0.9rem;
  }
}

/* Dark mode support for the overall portfolio */
.dark-mode .write-me-section {
  background: #000000;
}

.dark-mode .section-title {
  color: #f1f5f9;
}

.dark-mode .icon-text {
  color: #f1f5f9;
}

.dark-mode .icon-description {
  color: #cbd5e1;
}

.dark-mode .mail-icon {
  /* No background or border in dark mode */
}
</style>