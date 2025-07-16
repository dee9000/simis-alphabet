<template>
  <div class="card-wrapper">
    <div class="word-card">
      <!-- Image area -->
      <div class="image-container">
          <!-- 🅰️ Letter badge (top corner) -->
        <div class="letter-badge animate__animated animate__rotateIn">{{ letter }}</div>
        <img :src="image" :alt="word" class="word-image" />

        <!-- Hear it button inside image -->
        <button @click="playSound" class="sound-button">
          🔊 Hear it
        </button>
      </div>

      <!-- Navigation under the image -->
      <div class="navigation">
        <button @click="onPrev" :disabled="disablePrev">⬅ Back</button>
        <button @click="onNext" :disabled="disableNext">Next ➡</button>
      </div>

      <!-- Word below everything -->
      <h2 class="word-title">{{ word }}</h2>
    </div>
  </div>
</template>

<script setup>
const props = defineProps({
  image: String,
  word: String,
  audio: String,
  onNext: Function,
  onPrev: Function,
  disableNext: Boolean,
  disablePrev: Boolean,
  letter: String

})

const playSound = () => {
  const sound = new Audio(props.audio)
  sound.play()
}
</script>

<style scoped>
.card-wrapper {
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 90vh;
  background-color: #fefefe;
}

.word-card {
  background-color: #fff;
  border-radius: 24px;
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.06);
  text-align: center;
  max-width: 360px;
  padding: 20px;
}

.image-container {
  position: relative;
  width: 100%;
  height:50vh;
}

.word-image {
  width: 100%;
  height: auto;
  border-radius: 20px;
  display: block;
  padding-top: 3rem;
}

/* Red glossy pill button */
.sound-button {
  position: absolute;
  bottom: -25px;
  left: 50%;
  transform: translateX(-50%);
  font-size: 1rem;
  padding: 10px 24px;
  border-radius: 999px;
  background: linear-gradient(to top, #ff6b6b, #ff9b9b);
  color: white;
  border: none;
  cursor: pointer;
  font-weight: 500;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
  transition: all 0.2s ease;
}

.sound-button:hover {
  background: linear-gradient(to top, #e34747, #ff7e7e);
}

.navigation {
  display: flex;
  justify-content: space-between;
  margin-top: 36px;
  gap: 12px;
}

.navigation button {
  flex: 1;
  font-size: 1rem;
  padding: 10px;
  border-radius: 999px;
  border: none;
  background-color: #ffd6d6;
  color: #5a2a2a;
  cursor: pointer;
  font-weight: 500;
  transition: background-color 0.2s ease;
}

.navigation button:hover:not(:disabled) {
  background-color: #ffb6b6;
}

.navigation button:disabled {
  opacity: 0.4;
  cursor: not-allowed;
}

.word-title {
  font-size: 2rem;
  font-weight: 600;
  color: #222;
  margin-top: 20px;
}

.letter-badge {
  position: absolute;
  top: 1px;
  left: 1px;
  width: 100px;
  height: 100px;
  background: linear-gradient(to top, #efab01, #ffd277); /* soft sheen */
  color: white;
  font-size: 4rem;
  font-weight: 700;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  box-shadow:
    0 4px 12px rgba(0, 0, 0, 0.12), /* soft outer shadow */
    inset 0 4px 8px rgba(255, 255, 255, 0.15); /* inner top gloss */
  text-shadow: 0 2px 3px rgba(0, 0, 0, 0.2);
  z-index: 2;
  overflow: hidden;
  transition: all 0.3s ease;
}

</style>
