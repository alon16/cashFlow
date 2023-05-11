<template>
  <div>
    <svg
      @touchstart="tap"
      @touchmove="tap"
      @touchend="untap"
      viewBox="0 0 300 200"
    >
      <line
        stroke="#c4c4c4"
        stroke-width="2"
        x1="0"
        :y1="zero"
        x2="300"
        :y2="zero"
      />
      <polyline
        fill="none"
        stroke="#0689b9"
        stroke-width="2"
        :points="points"
      />
      <line
        v-show="showPointer"
        stroke="#04b500"
        stroke-width="2"
        :x1="pointerCoordenada"
        y1="0"
        :x2="pointerCoordenada"
        y2="200"
      />
    </svg>
    <p>Últimos 30 días</p>
  </div>
</template>
<script setup>
import { computed, defineProps, ref } from "vue";
const props = defineProps({
  amounts: {
    type: Array,
    default: () => [],
  },
});
const amountToPixels = (amount) => {
  const min = Math.min(...props.amounts);
  const max = Math.max(...props.amounts);
  const amountAbs = amount + Math.abs(min);
  const minMax = Math.abs(max) + Math.abs(min);
  return 200 - ((amountAbs * 100) / minMax) * 2;
};
const zero = computed(() => {
  return amountToPixels(0);
});
const points = computed(() => {
  const total = props.amounts.length;
  return props.amounts.reduce((points, amount, i) => {
    let x = (300 / total) * (i + 1);
    let y = amountToPixels(amount);
    return `${points} ${x},${y}`;
  }, "0,100");
});
let showPointer = ref(false);
let pointerCoordenada = ref(0);
const tap = ({ target, touches }) => {
  showPointer.value = true;
  let elementWidth = target.getBoundingClientRect().width;
  let elementX = target.getBoundingClientRect().x;
  let touchX = touches[0].clientX;
  pointerCoordenada.value = ((touchX - elementX) * 300) / elementWidth;
};
const untap = () => {
  showPointer.value = false;
};
</script>

<style scoped>
svg {
  width: 100%;
}

p {
  text-align: center;
}
</style>
