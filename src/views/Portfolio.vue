<script lang="ts">
import PortfolioCard from "./components/PortfolioCard.vue";

export default {
  components: {
    PortfolioCard,
  },
};
</script>

<template>
  <main>
    <h1>My QA automation projects</h1>
    <div class="portfolio">
      <PortfolioCard />
      <PortfolioCard />
      <PortfolioCard />
      <PortfolioCard />
      <PortfolioCard />
    </div>
    <h1>My QA automation projects</h1>
    <div class="portfolio">
      <PortfolioCard />
      <PortfolioCard />
      <PortfolioCard />
      <PortfolioCard />
      <PortfolioCard />
    </div>
  </main>
</template>

<style>
.portfolio {
  min-height: 100vh;
  display: flex;
  flex-wrap: wrap;
}

main {
  margin-top: 50px;
}
</style>
