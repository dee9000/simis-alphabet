<template>
  <div class="home">
    <h1>Welcome to Simi’s Word App 👧🏽</h1>
    <p>Tap “Start” to begin learning fun words!</p>
    <router-link to="/game">
      <button class="start-button">Start</button>
    </router-link>
  </div>
</template>

<script setup>
// No logic yet – just UI
</script>

<style scoped>
.home {
  text-align: center;
  padding-top: 50px;
}
.start-button {
  font-size: 1.5rem;
  padding: 12px 24px;
  background-color: #ffb703;
  border: none;
  border-radius: 8px;
  cursor: pointer;
}
</style>
