<template>
  <div class="chatbot-container">
    <!-- Chatbot Toggle Button -->
    <div v-if="!isOpen" @click="toggleChat" class="chat-toggle-btn">
      <svg width="28" height="28" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path d="M21 15C21 15.5304 20.7893 16.0391 20.4142 16.4142C20.0391 16.7893 19.5304 17 19 17H7L3 21V5C3 4.46957 3.21071 3.96086 3.58579 3.58579C3.96086 3.21071 4.46957 3 5 3H19C19.5304 3 20.0391 3.21071 20.4142 3.58579C20.7893 3.96086 21 4.46957 21 5V15Z" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
      </svg>
    </div>

    <!-- Chatbot Window -->
    <div v-if="isOpen" class="chat-window">
      <div class="chat-header">
        <div class="chat-title">
          <div class="assistant-info">
            <div class="assistant-avatar">
              <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M20 21V19C20 17.9391 19.5786 16.9217 18.8284 16.1716C18.0783 15.4214 17.0609 15 16 15H8C6.93913 15 5.92172 15.4214 5.17157 16.1716C4.42143 16.9217 4 17.9391 4 19V21" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                <circle cx="12" cy="7" r="4" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
              </svg>
            </div>
            <div>
              <h4>Jagarapu Radha Krishna Assistant</h4>
              <span class="status-text">Ask me anything about my portfolio!</span>
            </div>
          </div>
        </div>
        <button @click="toggleChat" class="close-btn">
          <svg width="20" height="20" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
            <line x1="18" y1="6" x2="6" y2="18" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
            <line x1="6" y1="6" x2="18" y2="18" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
          </svg>
        </button>
      </div>

      <div class="chat-messages" ref="messagesContainer">
        <div v-for="message in messages" :key="message.id" :class="['message', message.type]">
          <div class="message-content">
            {{ message.text }}
          </div>
          <div class="message-time">{{ message.time }}</div>
        </div>
      </div>

      <div class="chat-input-container">
        <input 
          v-model="newMessage" 
          @keypress.enter="sendMessage"
          placeholder="Type your message..."
          class="chat-input"
        >
        <button @click="sendMessage" class="send-btn">
          <svg width="20" height="20" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
            <line x1="22" y1="2" x2="11" y2="13" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
            <polygon points="22,2 15,22 11,13 2,9 22,2" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
          </svg>
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Chatbot',
  data() {
    return {
      isOpen: false,
      newMessage: '',
      messages: [
        {
          id: 1,
          type: 'bot',
          text: 'Hello! I\'m Jagarapu Radha Krishna\'s AI Assistant. How can I help you today?',
          time: this.getCurrentTime()
        }
      ]
    }
  },
  methods: {
    toggleChat() {
      this.isOpen = !this.isOpen;
    },
    sendMessage() {
      if (this.newMessage.trim()) {
        // Add user message
        this.messages.push({
          id: Date.now(),
          type: 'user',
          text: this.newMessage,
          time: this.getCurrentTime()
        });

        const userMessage = this.newMessage.toLowerCase();
        this.newMessage = '';

        // Auto-scroll to bottom
        this.$nextTick(() => {
          this.scrollToBottom();
        });

        // Bot response after a short delay
        setTimeout(() => {
          this.addBotResponse(userMessage);
        }, 1000);
      }
    },
    addBotResponse(userMessage) {
      let response = '';

      // Skills and expertise
      if (userMessage.includes('skill') || userMessage.includes('technology') || userMessage.includes('tech stack') || userMessage.includes('language')) {
        response = "I'm proficient in Java, JavaScript, Python, Vue.js, React, Node.js, Express, MongoDB, MySQL, Spring Boot, and cloud technologies like AWS. I also have experience with system design, DSA, and API development.";
      }
      // Education
      else if (userMessage.includes('education') || userMessage.includes('degree') || userMessage.includes('study') || userMessage.includes('college') || userMessage.includes('university')) {
        response = "I completed my B.Tech in Computer Science and Engineering from Amrita School of Engineering, Bangalore (2020-2024) with a CGPA of 8.24. I'm currently pursuing my Master's degree.";
      }
      // Projects
      else if (userMessage.includes('project') || userMessage.includes('work') || userMessage.includes('build') || userMessage.includes('developed')) {
        response = "I've worked on several exciting projects including NxtHire (job portal), Blood Donation Web App, Insurance Management System, FreshMenu clone, and various full-stack applications. Each project showcases different aspects of my technical skills.";
      }
      // Experience
      else if (userMessage.includes('experience') || userMessage.includes('internship') || userMessage.includes('job') || userMessage.includes('career')) {
        response = "I have experience as a Software Developer Intern and have worked on multiple full-stack projects. I'm passionate about creating efficient, user-friendly applications and constantly learning new technologies.";
      }
      // Contact information
      else if (userMessage.includes('contact') || userMessage.includes('email') || userMessage.includes('reach') || userMessage.includes('hire')) {
        response = "You can reach me at radhakrishna02256@gmail.com or connect with me through the contact form on this portfolio. I'm always open to discussing new opportunities!";
      }
      // About me / personal
      else if (userMessage.includes('about') || userMessage.includes('who') || userMessage.includes('tell me') || userMessage.includes('yourself')) {
        response = "I'm Jagarapu Radha Krishna, a passionate full-stack developer with expertise in modern web technologies. I love building innovative solutions and am always eager to take on new challenges in software development.";
      }
      // Resume/CV
      else if (userMessage.includes('resume') || userMessage.includes('cv') || userMessage.includes('download')) {
        response = "You can download my resume from the portfolio. It contains detailed information about my skills, projects, and experience. Feel free to check it out!";
      }
      // Certifications
      else if (userMessage.includes('certificate') || userMessage.includes('certification') || userMessage.includes('course')) {
        response = "I have completed various certifications in full-stack development, cloud computing, and modern web technologies. These help me stay updated with the latest industry trends.";
      }
      // Hello/Hi/Greetings
      else if (userMessage.includes('hello') || userMessage.includes('hi') || userMessage.includes('hey') || userMessage.includes('good morning') || userMessage.includes('good afternoon') || userMessage.includes('good evening')) {
        response = "Hello! I'm Radha Krishna's AI assistant. I'm here to help you learn more about my background, skills, projects, and experience. What would you like to know?";
      }
      // Thank you
      else if (userMessage.includes('thank') || userMessage.includes('thanks')) {
        response = "You're welcome! Feel free to ask me anything else about my portfolio, skills, or projects. I'm here to help!";
      }
      // Default response
      else {
        response = "That's an interesting question! I can help you with information about my skills, projects, education, experience, or contact details. What specific aspect would you like to know more about?";
      }

      this.messages.push({
        id: Date.now(),
        type: 'bot',
        text: response,
        time: this.getCurrentTime()
      });

      this.$nextTick(() => {
        this.scrollToBottom();
      });
    },
    getCurrentTime() {
      return new Date().toLocaleTimeString([], { hour: '2-digit', minute: '2-digit' });
    },
    scrollToBottom() {
      const container = this.$refs.messagesContainer;
      if (container) {
        container.scrollTop = container.scrollHeight;
      }
    }
  }
}
</script>

<style scoped>
.chatbot-container {
  position: fixed;
  bottom: 20px;
  right: 20px;
  z-index: 1000;
}

.chat-toggle-btn {
  width: 60px;
  height: 60px;
  background: linear-gradient(135deg, #333333 0%, #1a1a1a 100%);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.5);
  transition: all 0.3s ease;
  color: white;
  border: 2px solid #444444;
}

.chat-toggle-btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 12px 35px rgba(0, 0, 0, 0.7);
  background: linear-gradient(135deg, #444444 0%, #2a2a2a 100%);
}

.chat-window {
  width: 350px;
  height: 500px;
  background: #000000;
  border-radius: 16px;
  box-shadow: 0 25px 50px rgba(0, 0, 0, 0.4);
  border: 1px solid #333333;
  display: flex;
  flex-direction: column;
  overflow: hidden;
}

.chat-header {
  background: #1a1a1a;
  padding: 16px 20px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  border-bottom: 1px solid #333333;
}

.chat-title {
  flex: 1;
}

.assistant-info {
  display: flex;
  align-items: center;
  gap: 12px;
}

.assistant-avatar {
  width: 40px;
  height: 40px;
  background: #64748b;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #0f172a;
}

.assistant-info h4 {
  color: #e2e8f0;
  margin: 0;
  font-size: 1rem;
  font-weight: 600;
}

.status-text {
  color: #94a3b8;
  font-size: 0.8rem;
  display: block;
  margin-top: 2px;
}

.close-btn {
  background: none;
  border: none;
  color: #94a3b8;
  cursor: pointer;
  padding: 4px;
  border-radius: 4px;
  transition: all 0.2s ease;
}

.close-btn:hover {
  background: #475569;
  color: #e2e8f0;
}

.chat-messages {
  flex: 1;
  padding: 16px;
  overflow-y: auto;
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.chat-messages::-webkit-scrollbar {
  width: 4px;
}

.chat-messages::-webkit-scrollbar-track {
  background: #1e293b;
}

.chat-messages::-webkit-scrollbar-thumb {
  background: #334155;
  border-radius: 2px;
}

.message {
  display: flex;
  flex-direction: column;
}

.message.user {
  align-items: flex-end;
}

.message.bot {
  align-items: flex-start;
}

.message-content {
  max-width: 80%;
  padding: 12px 16px;
  border-radius: 12px;
  font-size: 0.9rem;
  line-height: 1.4;
}

.message.user .message-content {
  background: linear-gradient(135deg, #3b82f6 0%, #1d4ed8 100%);
  color: white;
  border-bottom-right-radius: 4px;
}

.message.bot .message-content {
  background: #1e293b;
  color: #e2e8f0;
  border-bottom-left-radius: 4px;
}

.message-time {
  font-size: 0.7rem;
  color: #94a3b8;
  margin-top: 4px;
  padding: 0 8px;
}

.chat-input-container {
  padding: 16px;
  background: #1e293b;
  border-top: 1px solid #334155;
  display: flex;
  gap: 8px;
}

.chat-input {
  flex: 1;
  padding: 12px 16px;
  background: #0f172a;
  border: 1px solid #334155;
  border-radius: 24px;
  color: #e2e8f0;
  font-size: 0.9rem;
  outline: none;
  transition: all 0.3s ease;
}

.chat-input:focus {
  border-color: #3b82f6;
  box-shadow: 0 0 0 3px rgba(59, 130, 246, 0.1);
}

.chat-input::placeholder {
  color: #94a3b8;
}

.send-btn {
  width: 40px;
  height: 40px;
  background: linear-gradient(135deg, #3b82f6 0%, #1d4ed8 100%);
  border: none;
  border-radius: 50%;
  color: white;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: all 0.2s ease;
}

.send-btn:hover {
  transform: scale(1.05);
}

@media (max-width: 768px) {
  .chatbot-container {
    bottom: 15px;
    right: 15px;
  }

  .chat-window {
    width: 320px;
    height: 450px;
  }

  .chat-toggle-btn {
    width: 55px;
    height: 55px;
  }
}
</style>