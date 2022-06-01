<script lang="ts">
export default {
  name: "Home",
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
};
</script>

<template>
  <div class="home">
    <div class="profile-pic">
      <img
        src="../assets/images/photo.png"
        alt="profile_picture"
        class="profile-image"
      />
    </div>
    <div class="profile-info">
      <h1><span>Hi, I'm Oscar</span> 👋</h1>
      <h2>I'm QA Automation Engineer and Full Stack Developer</h2>
      <ul class="skills-list">
        <li>
          📍 Located in Colombia
          <div class="col_flag"></div>
        </li>
        <li>🎒 QA Automation Engineer at EPAM</li>
      </ul>
      <div class="portfolio-social-media">
        <a
          href="https://www.linkedin.com/in/oscar-fabian-arias-rodriguez-b02241144/"
          target="_blank"
          ><i class="lni lni-linkedin-original"></i
        ></a>
        <a href="https://github.com/OscF95" target="_blank"
          ><i class="lni lni-github-original"></i
        ></a>
        <a @click="redirectToSendEmail"><i class="lni lni-envelope"></i></a>
      </div>
    </div>
  </div>
</template>

<style>
h1 {
  font-size: 3rem;
}
h2 {
  font-weight: bold;
}
.home {
  min-height: 89vh;
  display: flex;
  align-items: center;
  flex-direction: row;
  flex: 1 1;
  position: relative;
  z-index: 1;
  width: 90vw;
  margin: 1rem auto;
}
.profile-pic {
  width: 50vh;
  height: 50vh;
  border-radius: 50%;
  margin: 0px 48px 16px 0px;
  background: linear-gradient(135deg, rgb(12, 74, 115), rgb(154, 210, 244));
  box-shadow: 0 1rem 2rem rgb(0 0 0 / 40%);
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
