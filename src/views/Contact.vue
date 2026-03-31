<template>
  <a-layout-content class="contact-content">
    <h1 class="contact-header">Get In Touch</h1>
    <p class="contact-instruction">
      Feel free to reach out for any inquiries or collaborations!
    </p>
    
    <a-row justify="center">
      <a-col :xs="24" :sm="20" :md="16" :lg="12">
        <a-card class="contact-card" :bordered="false">
          <a-space direction="vertical" size="middle" style="width: 100%">
            <div class="contact-item">
              <div class="icon-box">
                <MailOutlined />
              </div>
              <div class="contact-details">
                <span class="contact-label">Email</span>
                <a href="mailto:annemarizdelacruz@gmail.com" class="contact-value">
                  annemarizdelacruz@gmail.com
                </a>
              </div>
            </div>
            
            <div class="contact-item">
              <div class="icon-box">
                <PhoneOutlined />
              </div>
              <div class="contact-details">
                <span class="contact-label">Phone</span>
                <a href="tel:+639764047137" class="contact-value">
                  (+63) 976 404 7137
                </a>
              </div>
            </div>
            
            <div class="contact-item">
              <div class="icon-box">
                <LinkedinOutlined />
              </div>
              <div class="contact-details">
                <span class="contact-label">LinkedIn</span>
                <a href="https://linkedin.com/in/amadc" target="_blank" class="contact-value">
                  linkedin.com/in/amadc
                </a>
              </div>
            </div>
            
            <div class="contact-item">
              <div class="icon-box">
                <EnvironmentOutlined />
              </div>
              <div class="contact-details">
                <span class="contact-label">Location</span>
                <span class="contact-value">Manila, Philippines</span>
              </div>
            </div>
          </a-space>
        </a-card>
      </a-col>
    </a-row>
  </a-layout-content>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import { MailOutlined, PhoneOutlined, LinkedinOutlined, EnvironmentOutlined } from "@ant-design/icons-vue";
import AOS from "aos";
import "aos/dist/aos.css";

export default defineComponent({
  name: "Contact",
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
  mounted() {
    AOS.init({
      duration: 800,
      easing: 'ease-out-cubic',
    });
  },
});
</script>

<style scoped>
.contact-content {
  padding: 40px 20px;
}

.contact-header {
  text-align: center;
  color: var(--color-text);
  font-family: 'Inter', sans-serif;
  margin-bottom: 10px;
  font-size: 2.5em;
  font-weight: 700;
}

.contact-instruction {
  text-align: center;
  color: var(--color-text-secondary);
  margin-bottom: 40px;
  font-size: 1.1em;
}

.contact-card {
  background: var(--color-bg-card);
  border-radius: 24px;
  box-shadow: var(--shadow-xl);
  padding: 30px;
  position: relative;
  overflow: hidden;
}

.contact-card::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 4px;
  background: var(--gradient-primary);
}

.contact-item {
  display: flex;
  align-items: center;
  padding: 20px;
  background: var(--color-bg-secondary);
  border-radius: 16px;
  transition: all 0.3s ease;
}

.contact-item:hover {
  transform: translateX(8px);
  box-shadow: var(--shadow-lg);
}

.icon-box {
  width: 50px;
  height: 50px;
  border-radius: 12px;
  background: var(--gradient-primary);
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 22px;
  color: white;
  margin-right: 18px;
  flex-shrink: 0;
}

.contact-details {
  display: flex;
  flex-direction: column;
}

.contact-label {
  font-size: 0.8em;
  color: var(--color-text-secondary);
  text-transform: uppercase;
  letter-spacing: 1.5px;
  margin-bottom: 4px;
  font-weight: 600;
}

.contact-value {
  font-size: 1.1em;
  color: var(--color-text);
  font-weight: 600;
  text-decoration: none;
  transition: color 0.3s ease;
}

.contact-value:hover {
  color: var(--color-primary);
}

@media (max-width: 768px) {
  .contact-header {
    font-size: 2em;
  }
  
  .contact-item {
    padding: 15px;
  }
  
  .icon-box {
    width: 40px;
    height: 40px;
    font-size: 18px;
  }
  
  .contact-value {
    font-size: 1em;
  }
}
</style>