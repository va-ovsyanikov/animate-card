<script setup>
defineProps({
  isActive: {
    type: Boolean,
    default: false
  }
})
</script>
<template>
  <div class="card" :class="{ active: isActive }">
    <div class="front">
      <span class="number">12</span>
      <div class="suit">
        <img src="../assets/images/Vector.svg" alt="alt" />
      </div>
    </div>
    <div class="back"></div>
  </div>
</template>
<style scoped>
.card {
  /* width: 185px; */
  height: 276px;
  position: relative;
  perspective: 600px;
}
.front,
.back {
  position: absolute;
  width: 100%;
  height: 100%;
  left: 0;
  top: 0;
  border-radius: 20px;
  transition: transform 0.6s linear;
  backface-visibility: hidden;
}
.front {
  background-color: #fff;
  padding: 10px 20px;
  transform: rotateY(180deg);
}
.back {
  background-image: url(../assets/images/Pattern.png);
  border: 12px solid #555660;
  background-position: -3px -2px;
}
.number {
  font-weight: 600;
  font-size: clamp(2.25rem, 1.534rem + 3.05vw, 3rem);
  line-height: 57.61px;
}
.suit {
  margin-top: 10px;
}
.card.active .front {
  transform: rotateY(360deg);
}
.card.active .back {
  transform: rotateY(180deg);
}
@media screen and (max-width: 768px) {
  .card {
    height: clamp(13.75rem, 4.109rem + 26.6vw, 16.875rem);
  }
  .front {
    padding: clamp(0.438rem, -0.141rem + 1.6vw, 0.625rem)
      clamp(0.813rem, -0.537rem + 3.72vw, 1.25rem);
  }
  .suit {
    margin-top: 5px;
  }
  .suit img {
    width: 45px;
  }
  .back {
    border: 8px solid #555660;
    background-position: center -3px;
  }
  @media screen and (max-width: 580px) {
    .card {
      height: clamp(11.875rem, 8.445rem + 14.63vw, 13.75rem);
    }
    .suit {
      margin-top: 0;
    }
    .suit img {
      width: clamp(2.188rem, 1.044rem + 4.88vw, 2.813rem);
    }
  }
}
</style>
