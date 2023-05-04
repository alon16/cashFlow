<template>
  <div class="movement">
    <div class="content">
      <h4>{{ movement.title }}</h4>
      <p>{{ movement.description }}</p>
    </div>
    <div class="action">
      <img src="@/assets/trash-icon.svg" alt="borrar" @click="remove" />
      <p :class="[isNegative ? 'red' : 'green']">
        {{ amountCurrency }}
      </p>
    </div>
  </div>
</template>

<script setup>
const currencyFormatter = new Intl.NumberFormat("es-NI", {
  style: "currency",
  currency: "NIC",
});
import { defineProps, computed, defineEmits } from "vue";
const props = defineProps({
  movement: {
    type: Object,
    default: () => {},
  },
});
const emit = defineEmits(["remove"]);
const amountCurrency = computed(() =>
  currencyFormatter.format(props.movement.amount)
);
const remove = () => {
  emit("remove", props.movement.id);
};
const isNegative = computed(() => props.movement.amount < 0);
</script>
<style scoped>
.movement {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 100%;
  padding: 16px;
  background-color: #e6f9ff;
  border-radius: 8px;
  box-sizing: border-box;
}
.movement .content {
  width: 100%;
}
.movement .action {
  display: flex;
  justify-content: space-between;
  align-items: flex-end;
  flex-direction: column;
}
h4,
p {
  margin: 0;
  padding: 0;
}
h4 {
  margin-bottom: 8px;
}
.movement .action img {
  margin-bottom: 16px;
}
.red {
  color: red;
}
.green {
  color: green;
}
</style>
