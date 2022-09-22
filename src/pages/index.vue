<script setup lang="ts">
import glugSfx from '../assets/button.wav'

const karmas = ref(0)
if (localStorage.getItem('karmas')) {
  karmas.value = Number(localStorage.getItem('karmas'))
}


const playSound = () => {
  const audio = new Audio(glugSfx)
  const text = document.getElementById('text') as HTMLElement
  audio.play()
  karmas.value++
  localStorage.setItem('karmas', karmas.value.toString())
  text.style.display = 'block'
  setTimeout(() => {
    text.style.display = 'none'
  }, 500)


}  
</script>

<template>
  <div py-4 />
  <span class="fixed left-0">今日累计功德 {{karmas}}</span>
  <div class="flex justify-center">
    <img class="m-3 img" src="../assets/1663870192330-ckt-抠图.png" @click="playSound()" />
    <div id="text" class="slide-out-top fixed">功德+1</div>
    <div />
  </div>
</template>


<style scoped>
#text {
  display: none;
}

.img:active {
  transform: scale(0.9);
  transition: all 0.1s ease-in-out;
}

.slide-out-top {
  -webkit-animation: slide-out-top 0.5s cubic-bezier(0.550, 0.085, 0.680, 0.530) both;
  animation: slide-out-top 0.5s cubic-bezier(0.550, 0.085, 0.680, 0.530) both;
}

@-webkit-keyframes slide-out-top {
  0% {
    -webkit-transform: translateY(0);
    transform: translateY(0);
    opacity: 1;
  }

  100% {
    -webkit-transform: translateY(-50px);
    transform: translateY(-50px);
    opacity: 0;
  }
}

@keyframes slide-out-top {
  0% {
    -webkit-transform: translateY(0);
    transform: translateY(0);
    opacity: 1;
  }

  100% {
    -webkit-transform: translateY(-50px);
    transform: translateY(-50px);
    opacity: 0;
  }
}
</style>