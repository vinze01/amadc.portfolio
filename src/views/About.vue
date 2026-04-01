<template>
  <a-layout-content class="about-content">
    <a-typography-title
      level="1"
      class="section-title"
      data-aos="fade-up"
    >
      About Me
    </a-typography-title>

    <a-typography-paragraph class="intro-text" data-aos="fade-up">
      I am a dedicated HR professional with a passion for people development and employee engagement. 
      With hands-on experience in human resources operations, I specialize in creating positive workplace 
      environments, managing employee relations, and ensuring HR compliance. My journey in HR has been 
      rewarding, allowing me to make meaningful contributions to organizational culture and employee well-being.
    </a-typography-paragraph>

    <a-divider class="divider" />

    <a-typography-title
      level="2"
      class="section-title"
      data-aos="fade-up"
    >
      Work Experience
    </a-typography-title>

    <a-timeline mode="left" class="experience-timeline">
      <a-timeline-item color="#ff69b4" data-aos="fade-up">
        <div class="experience-card">
          <div class="card-header">
            <h3 class="job-title">HR Specialist - Career Development</h3>
            <span class="duration-badge">April 2025 - Present</span>
          </div>
          <p class="company">
            <BankOutlined /> Enshored Inc.
          </p>
          <p class="location"><EnvironmentOutlined /> Pasig City, Philippines</p>
          
          <a-collapse :bordered="false" class="collapse-custom">
            <a-collapse-panel key="1" header="View Responsibilities">
              <div class="responsibilities">
                <ul>
                  <li>Request official rosters for quarterly performance reviews from HRIS</li>
                  <li>Creation of performance review templates for heroes, leaders, managers and up</li>
                  <li>Prepare, collect, and encode Quarterly Performance and Step-Up Performance Review results</li>
                  <li>Create and update Job Descriptions and Key Performance Indicators</li>
                  <li>Help HR Officer in facilitating Succession Planning</li>
                  <li>Perform any tasks that may be assigned from time to time</li>
                </ul>
              </div>
            </a-collapse-panel>
          </a-collapse>
        </div>
      </a-timeline-item>
      <a-timeline-item color="#ff69b4" data-aos="fade-up">
        <div class="experience-card">
          <div class="card-header">
            <h3 class="job-title">HR Assistant</h3>
            <span class="duration-badge">Feb 2023 - Jan 2025</span>
          </div>
          <p class="company">
            <BankOutlined /> SMC Mass Rail Transit 7 Inc. (San Miguel Corporation)
          </p>
          <p class="location"><EnvironmentOutlined /> Pasig City, Philippines</p>
          
          <a-collapse :bordered="false" class="collapse-custom">
            <a-collapse-panel key="1" header="View Responsibilities">
              <div class="responsibilities">
                <h4><TeamOutlined /> Administration</h4>
                <ul>
                  <li>Handled official communications, including office correspondence, memos, and announcements</li>
                  <li>Collaborated with building staff and support teams for operational requirements</li>
                  <li>Created and tracked purchase requisitions in SAP Ariba On-Demand</li>
                  <li>Monitored and managed budgets for office supplies and equipment</li>
                  <li>Implemented inventory management for medicine, pantry, and office supplies</li>
                </ul>
                
                <h4><DatabaseOutlined /> Employee Data Management</h4>
                <ul>
                  <li>Maintained employees' 201 files for HR compliance</li>
                  <li>Assisted with labor relations documentation</li>
                  <li>Maintained and updated employee performance and grading records</li>
                  <li>Monitored database of employees' Annual Physical Exam (APE) results</li>
                </ul>
                
                <h4><HeartOutlined /> Employee Engagement</h4>
                <ul>
                  <li>Led employee engagement activities (Valentine's Day, Halloween, birthdays, outreach programs)</li>
                  <li>Supported development and analysis of employee engagement surveys</li>
                  <li>Assisted with onboarding activities for new hires</li>
                  <li>Coordinated employee recognition programs</li>
                  <li>Organized workshops and training sessions</li>
                  <li>Led committees in planning annual company events</li>
                </ul>
                
                <h4><ReadOutlined /> Training and Development</h4>
                <ul>
                  <li>Acted as training coordinator for out-of-country trainings</li>
                  <li>Coordinated logistics for internal stakeholders and training providers</li>
                </ul>
                
                <h4><DollarOutlined /> Payroll, Benefits, and Timekeeping</h4>
                <ul>
                  <li>Monitored attendance and timekeeping for payroll processing</li>
                  <li>Managed employee applications for government statutory benefits</li>
                </ul>
                
                <h4><UserAddOutlined /> Recruitment</h4>
                <ul>
                  <li>Administered Aptitude Test and monitored pre-employment requirements</li>
                </ul>
              </div>
            </a-collapse-panel>
          </a-collapse>
        </div>
      </a-timeline-item>
    </a-timeline>

    <a-divider class="divider" />

    <a-typography-title
      level="2"
      class="section-title"
      data-aos="fade-up"
    >
      Education
    </a-typography-title>

    <a-card class="education-card" data-aos="fade-up">
      <a-row align="middle">
        <a-col :span="4">
          <div class="icon-wrapper">
            <BookOutlined class="education-icon" />
          </div>
        </a-col>
        <a-col :span="20">
          <h3 class="degree">Bachelor's Degree in Psychology – Cum Laude</h3>
          <p class="school"><BankOutlined /> Polytechnic University of the Philippines - Manila, Philippines</p>
          <p class="year">June 2018 to September 2022</p>
        </a-col>
      </a-row>
    </a-card>

    <a-divider class="divider" />

    <a-typography-title
      level="2"
      class="section-title"
      data-aos="fade-up"
    >
      Events, Workshops, Trainings & Seminars
    </a-typography-title>

    <div class="trainings-grid" data-aos="fade-up">
      <a-card v-for="(training, index) in trainings" :key="index" class="training-card" size="small">
        <div class="training-content">
          <CalendarOutlined class="training-icon" />
          <div class="training-details">
            <h4 class="training-title">{{ training.title }}</h4>
            <p class="training-org">{{ training.organization }}</p>
            <a-tag color="pink">{{ training.date }}</a-tag>
          </div>
        </div>
      </a-card>
    </div>
  </a-layout-content>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import { 
  BookOutlined, 
  CalendarOutlined,
  EnvironmentOutlined,
  TeamOutlined,
  DatabaseOutlined,
  HeartOutlined,
  ReadOutlined,
  DollarOutlined,
  UserAddOutlined,
  BankOutlined
} from "@ant-design/icons-vue";
import AOS from "aos";
import "aos/dist/aos.css";

export default defineComponent({
  name: "About",
  components: {
    BookOutlined,
    CalendarOutlined,
    EnvironmentOutlined,
    TeamOutlined,
    DatabaseOutlined,
    HeartOutlined,
    ReadOutlined,
    DollarOutlined,
    UserAddOutlined,
    BankOutlined,
  },
  props: {
    isDark: {
      type: Boolean,
      default: false
    }
  },
  data() {
    return {
      trainings: [
        {
          title: "Change Management in an Agile Environment",
          organization: "ARIVA Academy – Live Webinar",
          date: "July 4, 2023"
        },
        {
          title: "Enhancing Administrative Support Service Skills",
          organization: "ARIVA Academy – Live Webinar",
          date: "October 18, 2023"
        },
        {
          title: "Mandatory Payroll & Benefits Administration",
          organization: "Businessmaker Academy – Live Webinar",
          date: "October 26-27, 2023"
        },
        {
          title: "Professional HR Operations",
          organization: "Businessmaker Academy – Live Webinar",
          date: "January 25-26, 2024"
        },
        {
          title: "Onboarding & Employee Engagement",
          organization: "Businessmaker Academy – Live Webinar",
          date: "February 21, 2024"
        },
        {
          title: "Fundamentals of HR Management",
          organization: "Businessmaker Academy - Tektite Tower, Ortigas",
          date: "April 22, 2024"
        },
        {
          title: "Recruitment Management",
          organization: "Businessmaker Academy - Tektite Tower, Ortigas",
          date: "April 24, 2024"
        },
        {
          title: "Addressing Workplace Bullying and Harassment",
          organization: "ARIVA Academy – Live Webinar",
          date: "May 3, 2024"
        },
        {
          title: "How to Handle Toxic People at Work",
          organization: "ARIVA Academy – Live Webinar",
          date: "July 5, 2024"
        },
      ],
    };
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
.about-content {
  padding: 40px;
  background: transparent;
}

.section-title {
  text-align: center;
  color: var(--color-text);
  font-family: 'Inter', sans-serif;
  font-size: 2.5em;
  margin-bottom: 20px !important;
  font-weight: 700;
}

.intro-text {
  font-size: 18px;
  line-height: 1.8;
  text-align: center;
  max-width: 800px;
  margin: 0 auto 40px !important;
  color: var(--color-text-secondary);
}

.divider {
  border-color: var(--color-border);
  margin: 50px 0;
}

.experience-timeline {
  max-width: 900px;
  margin: 0 auto;
}

.experience-card {
  background: var(--color-bg-card);
  padding: 25px;
  border-radius: 20px;
  box-shadow: var(--shadow-lg);
  text-align: left;
  border: 1px solid var(--color-border);
}

.card-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-wrap: wrap;
  margin-bottom: 10px;
}

.job-title {
  font-size: 1.4em;
  color: var(--color-text);
  font-weight: 700;
  margin: 0;
}

.duration-badge {
  background: var(--gradient-primary);
  color: white;
  padding: 4px 12px;
  border-radius: 20px;
  font-size: 0.85em;
  font-weight: 500;
}

.company, .location {
  color: var(--color-text-secondary);
  font-size: 1em;
  margin-bottom: 5px;
  display: flex;
  align-items: center;
  gap: 6px;
}

.location {
  margin-bottom: 15px;
}

.collapse-custom {
  margin-top: 15px;
  background: transparent;
  border: none !important;
}

.collapse-custom :deep(.ant-collapse-header) {
  color: var(--color-primary) !important;
  font-weight: 600;
  border-radius: 10px !important;
  background: var(--color-bg-secondary);
}

.collapse-custom :deep(.ant-collapse-content-box) {
  padding: 15px 0 !important;
}

.responsibilities h4 {
  color: var(--color-text);
  font-weight: 600;
  margin-top: 15px;
  margin-bottom: 10px;
  display: flex;
  align-items: center;
  gap: 8px;
}

.responsibilities ul {
  margin-left: 20px;
  color: var(--color-text-secondary);
}

.responsibilities li {
  margin-bottom: 6px;
  line-height: 1.6;
}

.education-card {
  max-width: 700px;
  margin: 0 auto 40px;
  border-radius: 20px;
  box-shadow: var(--shadow-lg);
  border: 1px solid var(--color-border);
  background: var(--color-bg-card);
}

.icon-wrapper {
  width: 60px;
  height: 60px;
  border-radius: 50%;
  background: var(--gradient-primary);
  display: flex;
  align-items: center;
  justify-content: center;
}

.education-icon {
  font-size: 28px;
  color: white;
}

.degree {
  font-size: 1.3em;
  color: var(--color-text);
  font-weight: 700;
  margin-bottom: 8px;
}

.school {
  font-size: 1em;
  color: var(--color-text-secondary);
  margin-bottom: 5px;
  display: flex;
  align-items: center;
  gap: 6px;
}

.year {
  color: var(--color-text-secondary);
  font-size: 0.9em;
}

.trainings-grid {
  max-width: 900px;
  margin: 0 auto;
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
  gap: 15px;
}

.training-card {
  border-radius: 15px;
  border: 1px solid var(--color-border);
  background: var(--color-bg-card);
  transition: all 0.3s ease;
}

.training-card:hover {
  transform: translateY(-5px);
  box-shadow: var(--shadow-lg);
}

.training-content {
  display: flex;
  gap: 12px;
}

.training-icon {
  font-size: 24px;
  color: var(--color-primary);
  flex-shrink: 0;
}

.training-details {
  flex: 1;
}

.training-title {
  font-size: 0.95em;
  color: var(--color-text);
  font-weight: 600;
  margin-bottom: 5px;
  line-height: 1.4;
}

.training-org {
  font-size: 0.85em;
  color: var(--color-text-secondary);
  margin-bottom: 8px;
}

@media (max-width: 768px) {
  .section-title {
    font-size: 2em;
  }
  
  .trainings-grid {
    grid-template-columns: 1fr;
  }
  
  .card-header {
    flex-direction: column;
    align-items: flex-start;
    gap: 8px;
  }
}
</style>