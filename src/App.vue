<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: "App",
  data() {
    return {
      theme: "ligth-theme",
    };
  },
  mounted() {
    const theme = localStorage.getItem("theme");
    if (theme) {
      this.theme = theme;
      document.documentElement.className = theme;
      const hideCheckbox = document.getElementById("hide-checkbox") as HTMLInputElement | null;
      if (hideCheckbox) hideCheckbox.checked = false;
    }
  },
  methods: {
    setTheme(event: Event) {
      const target = event.target as HTMLInputElement;
      document.documentElement.className = target.checked ? "" : "dark-theme";
      localStorage.setItem("theme", document.documentElement.className);
      this.theme = document.documentElement.className;
    },
  },
});
</script>

<template>
  <header>
    <div class="nav-bar-container">
      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About Me</RouterLink>
        <RouterLink to="/portfolio">Portfolio</RouterLink>
        <RouterLink to="/blog">Blog</RouterLink>
      </nav>
      <div class="wrapper">
        <input
          type="checkbox"
          id="hide-checkbox"
          checked="true"
          @click="setTheme"
        />
        <label for="hide-checkbox" class="toggle">
          <span class="toggle-button">
            <span class="crater crater-1"></span>
            <span class="crater crater-2"></span>
            <span class="crater crater-3"></span>
            <span class="crater crater-4"></span>
            <span class="crater crater-5"></span>
            <span class="crater crater-6"></span>
            <span class="crater crater-7"></span>
          </span>
          <span class="star star-1"></span>
          <span class="star star-2"></span>
          <span class="star star-3"></span>
          <span class="star star-4"></span>
          <span class="star star-5"></span>
          <span class="star star-6"></span>
          <span class="star star-7"></span>
          <span class="star star-8"></span>
        </label>
      </div>
    </div>
  </header>
  <RouterView />
  <footer></footer>
</template>

<style>
@import "@/assets/base.css";
@import "@/assets/css/toggle_button.css";

#app {
  max-width: 1280px;
  margin: 0 auto;
  padding: 2rem;
  font-weight: normal;
}
.nav-bar-container {
  display: flex;
  justify-content: space-around;
}
nav a {
  text-decoration: none;
  padding: 15px;
  font-size: 25px;
}
</style>
