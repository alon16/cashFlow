<template>
  <div class="movement">{{ title }}</div>
</template>

<script setup>
import { defineProps } from "vue";
defineProps({
  title: {
    type: Array,
    default: () => [],
  },
});
</script>
