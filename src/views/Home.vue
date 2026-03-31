<template>
  <a-layout-content class="home-content">
    <a-row justify="center" style="text-align: center">
      <a-col :xs="24" :sm="22" :md="20" :lg="16">
        <div class="profile-container" data-aos="fade-up">
          <div class="profile-image-wrapper">
            <img src="@/assets/profile.jpg" alt="Profile Picture" class="profile-image" />
            <div class="profile-ring"></div>
          </div>
        </div>
        
        <h1 class="name-title" data-aos="fade-up" data-aos-delay="100">
          Anne Mariz A. Dela Cruz
        </h1>
        
        <div class="typing-effect" data-aos="fade-up" data-aos-delay="200">
          <span class="typing-text">{{ displayText }}</span>
          <span class="cursor">|</span>
        </div>
        
        <div class="contact-info" data-aos="fade-up" data-aos-delay="300">
          <a-space :size="16" wrap>
            <a href="mailto:annemarizdelacruz@gmail.com">
              <a-button class="contact-btn" shape="round">
                <MailOutlined /> annemarizdelacruz@gmail.com
              </a-button>
            </a>
            <a :href="'tel:+639764047137'">
              <a-button class="contact-btn" shape="round">
                <PhoneOutlined /> (+63) 976 404 7137
              </a-button>
            </a>
            <a href="https://linkedin.com/in/amadc" target="_blank">
              <a-button class="contact-btn" shape="round">
                <LinkedinOutlined /> LinkedIn
              </a-button>
            </a>
            <a-button class="contact-btn" shape="round">
              <EnvironmentOutlined /> Manila, Philippines
            </a-button>
          </a-space>
        </div>
        
        <router-link to="/about">
          <a-button type="primary" class="cta-button" data-aos="fade-up" data-aos-delay="400">
            Learn More About Me
          </a-button>
        </router-link>
      </a-col>
    </a-row>
  </a-layout-content>
</template>

<script lang="ts">
import { defineComponent, ref, onMounted } from "vue";
import { MailOutlined, PhoneOutlined, LinkedinOutlined, EnvironmentOutlined } from "@ant-design/icons-vue";
import AOS from "aos";
import "aos/dist/aos.css";

export default defineComponent({
  name: "Home",
  components: {
    MailOutlined,
    PhoneOutlined,
    LinkedinOutlined,
    EnvironmentOutlined,
  },
  props: {
    isDark: {
      type: Boolean,
      default: false
    }
  },
  setup() {
    const displayText = ref('');
    const fullText = 'HR Professional | People Champion | Career Development Specialist';
    let index = 0;

    onMounted(() => {
      AOS.init({
        duration: 800,
        easing: 'ease-out-cubic',
      });
      
      const typeInterval = setInterval(() => {
        if (index <= fullText.length) {
          displayText.value = fullText.slice(0, index);
          index++;
        } else {
          clearInterval(typeInterval);
        }
      }, 50);
    });

    return {
      displayText,
    };
  },
});
</script>

<style scoped>
.home-content {
  padding: 40px 20px;
}

.profile-container {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-bottom: 30px;
}

.profile-image-wrapper {
  position: relative;
  width: 240px;
  height: 240px;
}

.profile-image {
  width: 220px;
  height: 220px;
  border-radius: 50%;
  object-fit: cover;
  position: relative;
  z-index: 2;
  border: 4px solid var(--color-bg-card);
  transition: transform 0.3s ease;
}

.profile-ring {
  position: absolute;
  top: -10px;
  left: -10px;
  width: 240px;
  height: 240px;
  border-radius: 50%;
  background: var(--gradient-primary);
  z-index: 1;
  animation: pulse 3s ease-in-out infinite;
}

@keyframes pulse {
  0%, 100% { transform: scale(1); opacity: 0.8; }
  50% { transform: scale(1.05); opacity: 0.6; }
}

.profile-image:hover {
  transform: scale(1.05);
}

.name-title {
  font-size: 3em;
  background: var(--gradient-primary);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  font-weight: 700;
  margin-bottom: 15px;
  font-family: 'Inter', sans-serif;
}

.typing-effect {
  margin-bottom: 25px;
}

.typing-text {
  font-size: 1.3em;
  color: var(--color-text-secondary);
  font-weight: 500;
}

.cursor {
  animation: blink 1s step-end infinite;
  color: var(--color-primary);
}

@keyframes blink {
  50% { opacity: 0; }
}

.contact-info {
  margin-bottom: 30px;
}

.contact-btn {
  background: var(--color-bg-card) !important;
  border: 1px solid var(--color-border) !important;
  color: var(--color-text) !important;
  transition: all 0.3s ease;
  box-shadow: var(--shadow-sm);
}

.contact-btn:hover {
  background: var(--color-primary) !important;
  color: #fff !important;
  border-color: var(--color-primary) !important;
  transform: translateY(-3px);
  box-shadow: var(--shadow-md);
}

.cta-button {
  background: var(--gradient-primary) !important;
  border: none !important;
  padding: 12px 40px;
  font-size: 16px;
  height: auto;
  border-radius: 30px;
  font-weight: 600;
  transition: all 0.3s ease;
  box-shadow: var(--shadow-md);
}

.cta-button:hover {
  background: var(--color-primary-hover) !important;
  transform: translateY(-3px);
  box-shadow: var(--shadow-lg);
}

.social-icons {
  margin-top: 40px;
}

.social-icon {
  font-size: 24px;
  color: var(--color-text);
  transition: all 0.3s ease;
  display: flex;
  align-items: center;
  justify-content: center;
  width: 45px;
  height: 45px;
  border-radius: 12px;
  background: var(--color-bg-card);
  border: 1px solid var(--color-border);
  text-decoration: none;
}

.social-icon:hover {
  color: #fff !important;
  background: var(--gradient-primary);
  transform: translateY(-3px);
  box-shadow: var(--shadow-md);
}

@media (max-width: 768px) {
  .name-title {
    font-size: 2em;
  }
  
  .typing-text {
    font-size: 1em;
  }
  
  .profile-image-wrapper {
    width: 200px;
    height: 200px;
  }
  
  .profile-ring {
    width: 200px;
    height: 200px;
  }
  
  .profile-image {
    width: 180px;
    height: 180px;
  }
}
</style>