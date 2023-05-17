<template>
  <div class="movements">
    <h2 class="title">Historial</h2>
    <div class="content">
      <MovementsPage
        v-for="item in movements"
        :key="item.id"
        :movement="item"
        @removed="remove"
      />
    </div>
  </div>
</template>
<script setup>
import { defineProps, defineEmits } from "vue";
import MovementsPage from "./MovementPage.vue";
defineProps({
  movements: {
    type: Array,
    default: () => [],
  },
});
const emit = defineEmits(["removed"]);

const remove = (id) => {
  emit("removed", id);
};
</script>
vsetup
<style scoped>
.movements {
  max-height: 100%;
  padding: 0 8px;
  margin-bottom: 14px;
}
.title {
  margin: 8px 16px 24px 16px;
  color: var(--brand-blue);
}
.content {
  max-height: 68vh;
  display: flex;
  flex-direction: column;
  gap: 8px;
  overflow-y: scroll;
}
</style>
