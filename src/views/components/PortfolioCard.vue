<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'PortfolioCard',
});
</script>

<template>
  <div class="portfolio-card">
    <div class="card-blur"></div>
    <h2 class="card-text hidden-element">Project title</h2>
    <p class="card-text hidden-element">
      Lorem ipsum dolor sit amet consectetur, adipisicing elit. Quam nostrum
      quisquam quia repellendus, voluptas quis, modi quaerat aperiam assumenda
      veniam perspiciatis iusto voluptates commodi, rerum ullam? Perferendis
      iste repudiandae similique?
    </p>
    <div class="buttons hidden-element">
      <a href="https://github.com/OscF95" target="_blank"
        ><i class="lni lni-github-original"></i
      ></a>
      <a href="https://github.com/OscF95" target="_blank"
        ><i class="lni lni-play"></i
      ></a>
    </div>
  </div>
</template>

<style>
.hidden-element {
  visibility: hidden;
  opacity: 0;
  transition: opacity 2s;
  color: white;
}

.card-text {
  font-size: 1rem;
  padding: 5px;
  margin: auto;
}
.portfolio-card:hover .hidden-element {
  visibility: visible;
  opacity: 1;
}
.portfolio-card {
  background-image: url("https://upload.wikimedia.org/wikipedia/commons/thumb/f/f4/Code.org_logo.svg/1200px-Code.org_logo.svg.png");
  background-position: center;
  background-size: cover;
  background-repeat: no-repeat;
  flex: 1 0 calc(30% - 10px);
  height: 18rem;
  border-radius: 8px;
  margin: 5px;
  box-shadow: 0 1rem 2rem rgb(0 0 0 / 40%);
  overflow: hidden;
  display: inline-block;
}
.card-blur {
  position: absolute;
  height: 100%;
  width: calc(100% + 1px);
  background-color: black;
  opacity: 0;
  transition: opacity 0.15s ease-in;
}
.portfolio-card:hover .card-blur {
  opacity: 0.6;
}
h2 {
  font-weight: bold;
}
.lni {
  font-size: 2rem;
  margin: 5px;
}
.buttons {
  display: flex;
  justify-content: center;
  width: 100%;
}
</style>