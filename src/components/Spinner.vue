<template>
  <div class="spinner">
    <div
        v-for="(ring, index) in rings"
        :key="index"
        class="ring"
        :style="{
        width: ring + 'px',
        height: ring + 'px',
        animationDelay: index * 0.2 + 's'
      }"
    ></div>
    <div class="vinyl-center"></div>
    <div class="fixator-center"></div>
  </div>
</template>

<script>
export default {
  props: {
    animationRate: {type: Number},
  },
  data() {
    return {
      rings: [180, 160, 140, 120, 100, 80, 60]
    }
  }
}
</script>

<style>
.spinner {
  position: relative;
  width: 200px;
  height: 200px;
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 50%;
  background-color: #303030;
}

.ring {
  position: absolute;
  border: 1px solid rgba(255, 255, 255, 0.35);
  border-radius: 50%;
  animation: rotate 3s linear infinite;
}

.vinyl-center {
  position: absolute;
  background-image: linear-gradient(to top, red, yellow);
  width: 40px;
  height: 40px;
  border-radius: 50%;
  animation: rotate 3s linear infinite;
}

.fixator-center {
  position: absolute;
  background-color: #303030;
  width: 10px;
  height: 10px;
  border-radius: 50%;
}

@keyframes rotate {
  from { transform: rotate(0deg); }
  to { transform: rotate(360deg); }
}
</style>



