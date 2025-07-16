<script setup>
import { ref, computed } from 'vue'
import WordCard from '@/components/WordCard.vue'


import appleImage from '@/assets/Apple.png'
import appleAudio from '@/assets/Apple.mp3'
import ballImage from '@/assets/Ball.png'
import ballAudio from '@/assets/Ball.mp3'
import catImage from '@/assets/Cat.png'
import catAudio from '@/assets/cat.mp3'
import dogImage from '@/assets/Dog.png'
import dogAudio from '@/assets/dog.mp3'
import eggImage from '@/assets/egg.png'
import eggAudio from '@/assets/egg.mp3'
import fishImage from '@/assets/fish.png'
import fishAudio from '@/assets/fish.mp3'
import giraffeImage from '../assets/Giraffe.png'
import giraffeAudio from '../assets/Giraffe.mp3'
import houseImage from '../assets/House.png'
import houseAudio from '../assets/house.mp3'
import iceCreamImage from '../assets/ice-cream.png'
import iceCreamAudio from '../assets/ice-cream.mp3'
import jugImage from '../assets/Jug.png'
import jugAudio from '../assets/Jug.mp3'
import kiteImage from '../assets/Kite.png'
import kiteAudio from '../assets/Kite.mp3'
import lionImage from '../assets/Lion.png'
import lionAudio from '../assets/Lion.mp3'
import monkeyImage from '../assets/Monkey.png'
import monkeyAudio from '../assets/Monkey.mp3'
import nurseImage from '../assets/Nurse.png'
import nurseAudio from '../assets/Nurse.mp3'
import orangeImage from '../assets/Orange.png'
import orangeAudio from '../assets/Orange.mp3'
import potImage from '../assets/Pot.png'
import potAudio from '../assets/Pot.mp3'
import queenImage from '../assets/Queen.png'
import queenAudio from '../assets/Queen.mp3'
import rabbitImage from '../assets/Rabbit.png'
import rabbitAudio from '../assets/Rabbit.mp3'
import sunImage from '../assets/sun.png'
import sunAudio from '../assets/sun.mp3'
import turtleImage from '../assets/Turtle.png'
import turtleAudio from '../assets/Turtle.mp3'
import umbrellaImage from '../assets/Umbrella.png'
import umbrellaAudio from '../assets/Umbrella.mp3'
import violinImage from '../assets/Violin.png'
import violinAudio from '../assets/Violin.mp3'
import whaleImage from '../assets/Whale.png'
import whaleAudio from '../assets/Whale.mp3'
import xylophoneImage from '../assets/xylophone.png'
import xylophoneAudio from '../assets/Xylophone.mp3'
import yoyoImage from '../assets/Yoyo.png'
import yoyoAudio from '../assets/Yoyo.mp3'
import zebraImage from '../assets/Zebra.png'
import zebraAudio from '../assets/Zebra.mp3'




const words = [
   { image: appleImage, audio: appleAudio, word: 'Apple' },
   { image: ballImage, audio: ballAudio, word: 'Ball' },
   { image: catImage, audio: catAudio, word: 'Cat' },
   { image: dogImage, audio: dogAudio, word: 'Dog' },
   { image: eggImage, audio: eggAudio, word: 'Egg' },
   { image: fishImage, audio: fishAudio, word: 'Fish'},
   { image: giraffeImage, audio: giraffeAudio, word: 'Giraffe'},
   { image: houseImage, audio: houseAudio, word: 'House'},
   {image: iceCreamImage, audio: iceCreamAudio, word: 'Ice-Cream'},
   { image: jugImage, audio: jugAudio, word: 'Jug'},
   {image: kiteImage, audio: kiteAudio, word: 'Kite'},
   { image: lionImage, audio: lionAudio, word: 'Lion'},
   {image: monkeyImage, audio:monkeyAudio, word: 'Monkey'},
   { image: nurseImage, audio: nurseAudio, word: 'Nurse'},
   {image:orangeImage, audio: orangeAudio, word: 'Orange'},
   { image: potImage, audio: potAudio, word: 'Pot'},
   {image: queenImage, audio: queenAudio, word: 'Queen'},
   { image: rabbitImage, audio: rabbitAudio, word: 'Rabbit'},
   {image: sunImage, audio: sunAudio, word: 'Sun'},
   { image: turtleImage, audio: turtleAudio, word: 'Turtle'},
   {image: umbrellaImage, audio: umbrellaAudio, word: 'Umbrella'},
   { image: violinImage, audio:violinAudio, word: 'Violin'},
   {image: whaleImage, audio: whaleAudio, word: 'Whale'},
   { image: xylophoneImage, audio: xylophoneAudio, word: 'Xylophone'},
   {image: yoyoImage, audio: yoyoAudio, word: 'Yoyo'},
   { image: zebraImage, audio: zebraAudio, word: 'Zebra'}

      



]

const currentIndex = ref(0)
const currentWord = computed(() => words[currentIndex.value])

const nextWord = () => {
  if (currentIndex.value < words.length - 1) {
    currentIndex.value++
  }
}

const prevWord = () => {
  if (currentIndex.value > 0) {
    currentIndex.value--
  }
}
</script>


<template>
<WordCard
  :image="currentWord.image"
  :word="currentWord.word"
  :audio="currentWord.audio"
  :onNext="nextWord"
  :onPrev="prevWord"
  :disableNext="currentIndex === words.length - 1"
  :disablePrev="currentIndex === 0"
  :letter="currentWord.word.charAt(0)"

/>

</template>

<style scoped>
.game {
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 80vh;
  background-color: #f9f9f9; /* soft background */
}
</style>
