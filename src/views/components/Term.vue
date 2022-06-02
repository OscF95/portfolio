<script lang="ts">
export default {
  name: "Shell",
};
</script>

<template>
  <main class="term">
    <div class="term-header">
      <span class="button close-button"></span>
      <span class="button minimize-button"></span>
      <span class="button maximize-button"></span>
    </div>
    <div class="term-body">
      <p class="term-text route-term-text">
        ~/Documents/portfolio <span class="branch-term-text">(master)$ > </span>
        <span class="command-term-text">cat about_me.txt</span>
      </p>
      <br>
      <p class="term-text command-term-text">
        Hello! I'm Oscar. I studied Systems Enginering. I have 5+ years of experiece working as a QA Engineer, participating in different
        worldwide projects using different automation, CI/CD and ticket management tool. Different programming languages (mainly JS) and using agile metologies.
      </p>
    </div>  
  </main>
</template>

<style>
.term {
  background: black;
  width: 60vw;
  height: 90vh;
  border-radius: 10px;
  box-shadow: 0 1rem 2rem rgb(0 0 0 / 40%);
  margin-top: 50px;
}
.term-header {
  background: rgb(81, 80, 80);
  width: 100%;
  height: 8%;
  border-radius: 10px 10px 0 0;
  display: flex;
  align-items: center;
  padding: 8px;
}
.term-body {
  margin: 50px;
  height: 74%;
}
.button {
  width: 20px;
  height: 20px;
  border-radius: 50%;
  display: inline-block;
  margin: 5px;
}
.close-button {
  background: rgb(217, 88, 88);
}
.minimize-button {
  background: #ffbd2e;
}
.maximize-button {
  background: #27c93f;
}
.term-text {
  font-size: 30px;
  color: #27c93f;
  font-weight: bold;
  font-family: "Courier New", Courier, monospace;
}
.command-term-text {
  color: #f8f8f8;
}
.route-term-text {
  color: purple;
}
.branch-term-text {
  color: #27c93f;
}
</style>
