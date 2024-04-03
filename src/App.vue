<script setup>
import { ref } from 'vue'
import CardGame from '@/components/CardGame.vue'
import ButtonGame from '@/components/ButtonGame.vue'
const isActive = ref(false)
</script>

<template>
  <main>
    <div class="btn_down">
      <ButtonGame @onClick="isActive = false" :isDown="true" />
    </div>
    <CardGame
      v-for="i in 3"
      :isActive="isActive && i === 2"
      :class="{ animate: isActive && i === 2 }"
      :key="i"
    />
    <div class="btn_up">
      <ButtonGame @onClick="isActive = true" :isUp="true" />
    </div>
  </main>
</template>

<style scoped>
main {
  display: grid;
  grid-template-columns:
    minmax(64px, 90px) repeat(3, minmax(113px, 185px))
    minmax(64px, 90px);
  justify-content: center;
  align-items: center;
  column-gap: 1.3rem;
  width: 100%;
  margin: 0 2rem;
}
.btn_up {
  display: flex;
  justify-content: flex-end;
}
.animate {
  animation-duration: 1s;
  animation-name: animate;
  /* animation-iteration-count: 1; */
  animation-delay: 0.8s;
  animation-fill-mode: forwards;
}
@keyframes animate {
  0% {
    transform: translate(0, 0px);
  }
  100% {
    transform: translate(0, -300px);
  }
}
@media screen and (max-width: 768px) {
  main {
    position: fixed;
    bottom: -63px;
    column-gap: 1rem;
  }
  .btn_down {
    margin-left: 10px;
  }
  .btn_up {
    margin-right: 10px;
  }
}
@media screen and (max-width: 580px) {
  main {
    padding: 0 2rem;
    grid-template-columns: repeat(3, minmax(110px, 1fr));
  }
  .btn_down,
  .btn_up {
    position: absolute;
  }
  .btn_down {
    left: 0;
    z-index: 2;
  }
  .btn_up {
    right: 0;
  }
}
</style>
