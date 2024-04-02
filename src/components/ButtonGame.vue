<script setup>
import Up from '../assets/images/Up.svg'
import Down from '../assets/images/Down.svg'
defineProps({
  isUp: {
    type: Boolean,
    default: false
  },
  isDown: {
    type: Boolean,
    default: false
  }
})
</script>
<template>
  <div class="button" :class="{ up: isUp, down: isDown }" @click="$emit('onClick')">
    <img :src="isUp ? Up : Down" alt="alt" />
  </div>
</template>
<style scoped>
.button {
  width: 64px;
  height: 64px;
  border-radius: 50%;
  border: 4px solid transparent;
  color: #fff;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
}
.button.up {
  background-color: #71c658;
  border-color: #66ac52;
}
.button.down {
  background-color: #dd385f;
  border-color: #bc3353;
}
</style>
