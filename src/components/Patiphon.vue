<template>
  <div class="patiphon-box gofra">
    <spinner></spinner>
  </div>
</template>

<script>
import Spinner from "@/components/Spinner.vue";
export default {
  components: {
    Spinner
  },
  data () {
    return {
      width: 400,
      height: 250
    }
  }
}
</script>

<style scoped>
  .patiphon-box {
    padding: 10px 0 0 10px;
    width: 300px;
    height: 250px;
    border-radius: 5px;
  }
  .gofra {
    background: repeating-linear-gradient(
        90deg,
        #0b0b0b,
        #393737 5px,
        #000000 5px,
        #393737 10px
    );
    box-shadow: inset 0 5px 10px rgba(0,0,0,0.2);
  }
</style>
