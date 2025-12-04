<template>
  <div class="lever-block">
    <div class="lever" ref="leverBlock" :style="{
      transform: `translateX(-50%) rotate(${angle}deg)`,
    }" @mousedown='startDrag'>
      <div class="dot"></div>
      <div class="dot-fixation"></div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    modelValue: {type: Number, default: 0},
  },
  data () {
    return {
      dragging: false,
      angle: 0,
      modelValue: 0,
      intervalId: null,
      localValue: this.modelValue,
    }
  },
  emits: ['update:modelValue'],
  methods: {
    startDrag () {
      this.dragging = true
      window.addEventListener('mousemove', this.onDrag)
      window.addEventListener('mouseup', this.stopDrag)
      this.startProgressTimer()
    },
    startProgressTimer() {
      // защищаемся от дублирования интервалов
      if (this.intervalId) return

      this.intervalId = setInterval(() => {
        this.modelValue++
        this.$emit('update:modelValue', this.modelValue)
      }, 2000)
    },
    onDrag(e) {
      if (!this.dragging) return

      const rect = this.$refs.leverBlock.getBoundingClientRect()
      const centerX = rect.left + rect.width / 2
      const centerY = rect.bottom

      const dx = e.clientX - centerX
      const dy = e.clientY - centerY // инвертируем Y для инверсии направления

      // вычисляем угол в градусах, инвертированное направление
      let newAngle = Math.atan2(dy, dx) * (180 / Math.PI)

      // приводим угол к диапазону 0–360°
      if (newAngle < 0) newAngle += 360

      this.angle = newAngle

      console.log(this.modelValue)
    },
    stopDrag() {
      this.dragging = false
      window.removeEventListener('mousemove', this.onDrag)
      window.removeEventListener('mouseup', this.stopDrag)
      clearInterval(this.intervalId)
      this.intervalId = null
    }
  },
  watch: {
    modelValue (v) {
      this.localValue = v
    }
  }
}
</script>

<style scoped>
  .lever-block {
    position: relative;
    width: 30px;       /* ширина блока рычага */
    height: 200px;     /* высота блока рычага */
    padding: 15px;
  }
  .lever {
    position: absolute;
    width: 5px;
    height: 15%;
    background-color: #f2f2f2;
    bottom: 20%;
    left: 50%;
    transform: translateX(-50%);
    transform-origin: bottom center;
    border-radius: 5px;
    cursor: grab;
  }

  .rotation {
    animation: rotate 3s infinite linear;
  }

  .dot {
    position: absolute;
    top: 0; /* расположение наверху рычага */
    left: 50%;
    transform: translate(-50%, -50%); /* чтобы центр точки совпадал с верхом рычага */
    height: 10px;  /* размер точки */
    width: 10px;
    border-radius: 50%;
    background-color: brown;
  }

  .dot-fixation {
    position: absolute;
    bottom: 0;
    left: 50%;
    right: 50%;
    transform: translate(-60%, 10%);
    height: 5px;
    width: 5px;
    border-radius: 50%;
    background-color: #000000;
  }

  @keyframes rotate {
    from { transform: rotate(0deg); }
    to { transform: rotate(360deg); }
  }
</style>
