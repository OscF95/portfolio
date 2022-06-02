<script lang="ts">
import Term from "./components/Term.vue"

export default {
  components: {
    Term
  }
}
</script>

<template>
  <div class="about">
  <Term/>
  <Term/>
  </div>
</template>

<style>
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
    flex-direction: column;
  }
</style>
