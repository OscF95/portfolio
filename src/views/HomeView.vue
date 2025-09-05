<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  data() {
    return {
      email: "ofariasr1@gmail.com",
    };
  },
  methods: {
    redirectToSendEmail() {
      window.location.href = `mailto:${this.email}`;
    },
  },
});
</script>

<template>
  <div class="home">
    <div class="profile-pic">
      <img src="../assets/images/photo.png" alt="profile_picture" class="profile-image" />
    </div>
    <div>
      <h1><span>Hi, I'm Oscar</span></h1>
      <h2>Senior QA Automation Engineer and Game Developer enthusiast</h2>
      <ul class="skills-list">
        <li>
          📍 Located in Colombia 🇨🇴
        </li>
        <li>🎒 Senior QA Automation Engineer at Exadel</li>
      </ul>
    </div>
  </div>
  <footer>
    <div class="portfolio-social-media">
      <a href="https://www.linkedin.com/in/oscar-fabian-arias-rodriguez-b02241144/" target="_blank"><i
          class="lni lni-linkedin-original"></i></a>
      <a href="https://github.com/OscF95" target="_blank"><i class="lni lni-github-original"></i></a>
      <a @click="redirectToSendEmail"><i class="lni lni-envelope"></i></a>
    </div>
  </footer>
</template>

<style scoped>
h1 {
  font-size: 3rem;
}

h2 {
  font-weight: bold;
}

.home {
  min-height: 80vh;
  display: flex;
  align-items: center;
  flex-direction: row;
  flex: 1;
  position: relative;
  z-index: 1;
  box-sizing: border-box;
}

.profile-pic {
  width: 300px;
  height: auto;
  max-width: 100%;
  border-radius: 50%;
  background: linear-gradient(135deg, #4a9eff 0%, #78dce8 100%);
  display: flex;
  align-items: center;
  justify-content: center;
  transition: all 0.3s ease;
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.3);
  animation: float 6s ease-in-out infinite;
  margin: 0px 48px 16px 0px;
}

.profile-pic:hover {
  transform: scale(1.05);
  box-shadow: 0 25px 50px rgba(120, 220, 232, 0.3);
}

.profile-image {
  max-width: 100%;
  max-height: 100%;
  border-radius: 50%;
}

span {
  font-weight: bold;
}

.skills-list {
  list-style-type: none;
  margin: 10px 0 10px 0;
  padding: 0px;
  font-size: large;
}

.lni {
  font-size: 3rem;
}

.lni:hover {
  color: grey;
}

.portfolio-social-media {
  padding-top: 20px;
  display: flex;
  justify-content: space-evenly;
}

@media only screen and (max-width: 1230px) {
  .profile-pic {
    width: 34vh;
    height: 34vh;
  }
}

@media only screen and (max-width: 1056px) {
  .profile-pic {
    width: 30vh;
    height: 30vh;
  }
}

@media only screen and (max-width: 992px) {
  .home {
    flex-direction: column;
    justify-content: space-evenly;
  }
}
</style>
