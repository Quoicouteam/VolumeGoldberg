<template>
  <div class="patiphon-box gofra">
    <spinner
      :animation-rate="progress"
    ></spinner>
    <toneram/>
    <lever
        v-model="progress"
    ></lever>
  </div>
</template>

<script>
import Spinner from "@/components/Spinner.vue";
import Lever from "@/components/Lever.vue";
import Toneram from "@/components/Toneram.vue";
export default {
  components: {
    Spinner,
    Lever,
    Toneram,
  },
  data () {
    return {
      width: 400,
      height: 250,
      progress: 0
    }
  }
}
</script>

<style scoped>
.patiphon-box {
  padding: 10px 0 0 10px;
  width: 300px;
  height: 250px;
  border-radius: 8px;

  display: flex;
  justify-content: space-between;

  background: #1b1b1b;
  box-shadow:
      0 4px 12px rgba(0,0,0,0.5),
      inset 0 6px 12px rgba(255,255,255,0.05),
      inset 0 -6px 12px rgba(0,0,0,0.4);
}

.gofra {
  background: repeating-linear-gradient(
      90deg,
      #0e0e0e,
      #2c2c2c 5px,
      #000000 5px,
      #2c2c2c 10px
  );
}
</style>
