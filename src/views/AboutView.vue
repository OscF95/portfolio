<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  data() {
    return {
      commands: ['ls', 'cd projects', 'git status', 'npm test', 'vim README.md'],
      currentCommand: 0,
      currentChar: 0,
      typingText: ''
    };
  },
  mounted() {
    setTimeout(() => {
      this.typeCommand();
    }, 2000);
  },
  methods: {
    showOutput(outputId: string) {
      // Hide all outputs
      const outputs = document.querySelectorAll('.command-output');
      outputs.forEach(output => {
        output.classList.remove('show');
      });

      // Show selected output
      const targetOutput = document.getElementById(outputId + '-output');
      if (targetOutput) {
        targetOutput.classList.add('show');
      }
    },

    typeCommand() {
      if (this.currentChar < this.commands[this.currentCommand].length) {
        this.typingText += this.commands[this.currentCommand][this.currentChar];
        this.currentChar++;
        setTimeout(() => this.typeCommand(), 100);
      } else {
        setTimeout(() => {
          this.typingText = '';
          this.currentChar = 0;
          this.currentCommand = (this.currentCommand + 1) % this.commands.length;
          setTimeout(() => this.typeCommand(), 1000);
        }, 2000);
      }
    },

    getAgesOfExperience() {
      const startYear = 2016;
      const currentYear = new Date().getFullYear();
      const currentMonth = new Date().getMonth();
      if (currentMonth < 12) {
        return `${currentYear - startYear - 1}+`;
      }
      return currentYear - startYear;
    }
  }
});
</script>

<template>
  <div class="container">
    <div class="terminal-window">
      <div class="terminal-header">
        <div class="terminal-button close"></div>
        <div class="terminal-button minimize"></div>
        <div class="terminal-button maximize"></div>
        <div class="terminal-title">oscar@portfolio:~/about</div>
      </div>

      <div class="terminal-content">
        <div class="command-line">
          <span class="prompt">~/Documents/portfolio</span>
          <span class="path"></span>
          <span class="branch">(master)</span>
          <span>$ </span>
          <span class="command">cat about_me.txt</span>
        </div>

        <pre class="output file-content">
          <span class="comment"># About Oscar - Senior QA Automation Engineer</span>
          <span class="highlight">Name:</span> Oscar
          <span class="highlight">Role:</span> Senior QA Automation Engineer & Game Development Enthusiast
          <span class="highlight">Location:</span> Colombia 🇨🇴
          <span class="highlight">Company:</span> Exadel
          <span class="highlight">Experience:</span> {{ getAgesOfExperience() }} years in Quality Assurance

          <span class="comment">## Professional Summary</span>
          Hi, I'm Oscar! As a Systems Engineer with over {{ getAgesOfExperience() }} years in quality
          assurance, I've helped deliver reliable software solutions for
          international projects. I specialize in building robust test
          automation frameworks, implementing CI/CD processes, and driving
          quality initiatives using agile practices.

          <span class="comment">## Current Focus</span>
          - Test automation with JavaScript/TypeScript
          - CI/CD pipeline optimization
          - Game development with Unity & Godot
          - Mentoring junior QA engineers
          - Open source contributions

          <span class="comment">## Fun Stats</span>
          - <span class="string">Bugs found:</span> 10,000+
          - <span class="string">Countries worked with:</span> 15+
          - <span class="string">Games created:</span> 5+
          - <span class="string">Coffee cups/day:</span> ∞
  </pre>

        <div class="command-line">
          <span class="prompt">~/Documents/portfolio</span>
          <span class="branch">(master)</span>
          <span>$ </span>
          <span class="typing-animation">{{ typingText }}</span>
        </div>

        <div class="interactive-commands">
          <div class="available-commands"># Try these commands:</div>

          <button class="command-button" @click="showOutput('skills')">ls skills/</button>
          <button class="command-button" @click="showOutput('experience')">cat experience.log</button>
          <button class="command-button" @click="showOutput('projects')">find . -name "*.project"</button>
          <button class="command-button" @click="showOutput('contact')">whoami --contact</button>

          <div id="skills-output" class="command-output">
            <div class="command-line">
              <span class="prompt">~/Documents/portfolio</span>
              <span class="branch">(master)</span>
              <span>$ </span>
              <span class="command">ls skills/</span>
            </div>
            <div class="skills-grid">
              <div class="skill-item">🔧 automation/</div>
              <div class="skill-item">💻 javascript/</div>
              <div class="skill-item">🚀 devops/</div>
              <div class="skill-item">🎮 gamedev/</div>
              <div class="skill-item">🧪 testing/</div>
              <div class="skill-item">⚡ ci-cd/</div>
            </div>
          </div>

          <div id="experience-output" class="command-output">
            <div class="command-line">
              <span class="prompt">~/Documents/portfolio</span>
              <span class="branch">(master)</span>
              <span>$ </span>
              <span class="command">cat experience.log</span>
            </div>
            <pre class="file-content">
              <span class="comment">[2023-Present] Senior QA Automation Engineer & Team Lead - Exadel</span>
              - Leading a combined manual and automation QA team, mentoring and managing workload
              - Enhancing automation framework with WebdriverIO, Axios, and BDD (Gherkin)
              - Driving quality culture and continuous testing in Jenkins CI/CD pipelines

              <span class="comment">[2022-2023] Test Automation Engineer - Lereta LLC</span>
              - Migrated automation framework from .NET 4.7 to .NET Core 6
              - Automated UI and API test cases using Selenium, SpecFlow, and RestSharp with C#
              - Implemented Azure DevOps pipelines for consistent test execution

              <span class="comment">[2022] Test Automation Engineer - EPAM Anywhere</span>
              - Automated web UI test cases with WebdriverIO (TypeScript) and Playwright
              - Expanded automation coverage to mobile apps with Appium
              - Generated detailed reporting with Allure for stakeholder visibility

              <span class="comment">[2021-2022] Senior Test Automation Engineer - Overactive (Now part of Perficient)</span>
              - Built UI, API, and mobile test automation with Cypress, WebdriverIO, and Appium
              - Designed and executed K6 scripts for performance testing
              - Integrated automation into Azure DevOps CI/CD workflows

              <span class="comment">[2019-2021] Test Automation Engineer - Globant</span>
              - Established automation methodologies and frameworks
              - Automated API and UI testing with Selenium, NUnit, and RestSharp
              - Applied OOP and design patterns to improve maintainability of test code

              <span class="comment">[2018-2019] Test Automation Engineer - PSL (Now part of Perficient)</span>
              - Designed automation frameworks for web and mobile apps with Selenium, Appium, and Python
              - Created test plans and executed functional and regression tests
              - Integrated automation into Jenkins pipelines and optimized test environments with Docker

              <span class="comment">[2016-2018] Test Automation Engineer - Stefanini</span>
              - Designed and executed automated UI and mobile tests with Selenium, Appium, and Java
              - Conducted API testing with SoapUI and improved reliability
              - Ran JMeter performance testing and delivered reports to guide improvements
            </pre>
          </div>

          <div id="projects-output" class="command-output">
            <div class="command-line">
              <span class="prompt">~/Documents/portfolio</span>
              <span class="branch">(master)</span>
              <span>$ </span>
              <span class="command">find . -name "*.project"</span>
            </div>
            <pre class="file-content">
              ./automation/selenium-framework.project
              ./automation/cypress-dashboard.project
              ./gamedev/unity-2d-platformer.project
              ./gamedev/godot-rpg.project
              ./web/portfolio-website.project
              ./tools/test-data-generator.project

              <span class="comment"># Run 'cd projects && ls -la' to explore more!</span>
            </pre>
          </div>

          <div id="contact-output" class="command-output">
            <div class="command-line">
              <span class="prompt">~/Documents/portfolio</span>
              <span class="branch">(master)</span>
              <span>$ </span>
              <span class="command">whoami --contact</span>
            </div>
            <pre class="file-content">
              <span class="highlight">User:</span> oscar
              <span class="highlight">Email:</span> ofariasr1@gmail.com
              <span class="highlight">LinkedIn:</span> /in/oscar-fabian-arias-rodriguez-b02241144
              <span class="highlight">GitHub:</span> /OscF95
              <span class="highlight">Status:</span> Available for collaboration
              <span class="highlight">Timezone:</span> COT (UTC-5)
              <span class="highlight">Languages:</span> Spanish, English

              <span class="comment"># Always happy to connect with fellow developers! 🚀</span>
            </pre>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 40px 40px 40px;
}

.terminal-window {
  background: #1a1a1a;
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.3);
  border: 1px solid #333;
}

.terminal-header {
  background: #2d2d2d;
  padding: 12px 16px;
  display: flex;
  align-items: center;
  gap: 8px;
  border-bottom: 1px solid #333;
}

.terminal-button {
  width: 12px;
  height: 12px;
  border-radius: 50%;
}

.close {
  background: #ff5f57;
}

.minimize {
  background: #ffbd2e;
}

.maximize {
  background: #28ca42;
}

.terminal-title {
  margin-left: auto;
  margin-right: auto;
  color: #8e8e8e;
  font-size: var(--base-font-size);
}

.terminal-content {
  padding: 20px;
  background: #000;
  min-height: 500px;
  font-size: var(--base-font-size);
  line-height: 1.6;
  font-family: 'Courier New', 'Monaco', 'Menlo', monospace;
}

.command-line {
  display: flex;
  margin-bottom: 10px;
}

.prompt {
  color: #e91e63;
  margin-right: 10px;
}

.path {
  color: #9c27b0;
}

.branch {
  color: #4caf50;
}

.command {
  color: #00bcd4;
}

.output {
  color: #ffffff;
  margin-bottom: 20px;
  white-space: pre-wrap;
}

.typing-animation {
  border-right: 2px solid #00bcd4;
  animation: blink 1s infinite;
}

@keyframes blink {

  0%,
  50% {
    border-color: #00bcd4;
  }

  51%,
  100% {
    border-color: transparent;
  }
}

.file-content {
  color: #e0e0e0;
  line-height: 1.8;
  margin-bottom: 20px;
  white-space: pre-wrap;
}

.highlight {
  color: #78dce8;
  font-weight: bold;
}

.comment {
  color: #6a9955;
}

.string {
  color: #ce9178;
}

.interactive-commands {
  margin-top: 30px;
}

.available-commands {
  color: #6a9955;
  font-style: italic;
  margin-bottom: 15px;
}

.command-button {
  background: transparent;
  color: #00bcd4;
  border: 1px solid #00bcd4;
  padding: 8px 16px;
  margin: 5px 10px 5px 0;
  border-radius: 4px;
  cursor: pointer;
  font-family: inherit;
  font-size: var(--base-font-size);
  transition: all 0.3s ease;
}

.command-button:hover {
  background: rgba(0, 188, 212, 0.1);
  transform: scale(1.05);
}

.command-output {
  margin-top: 15px;
  padding: 15px;
  background: rgba(255, 255, 255, 0.05);
  border-left: 3px solid #78dce8;
  display: none;
}

.command-output.show {
  display: block;
  animation: fadeIn 0.5s ease;
}

@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(-10px);
  }

  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.skills-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 10px;
  margin: 15px 0;
}

.skill-item {
  color: #78dce8;
  padding: 5px 0;
}

@media (max-width: 768px) {
  .container {
    padding: 20px 20px 20px;
  }

  .terminal-content {
    font-size: var(--base-font-size);
    padding: 15px;
  }
}
</style>
