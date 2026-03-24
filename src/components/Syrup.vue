<template>
  <div class="syrup" :style="syrupStyle"></div>
</template>

<script setup lang="ts">
import { computed } from "vue";
import { syrups } from "../stores/beverage";

const props = defineProps<{
  syrup: string;
}>();

const selectedSyrup = computed(() =>
  syrups.value.find(s => s.id === props.syrup)
);

const syrupStyle = computed(() => ({
  backgroundColor: selectedSyrup.value?.color || "transparent"
}));
</script>

<style lang="scss" scoped>
.syrup {
  transform: translateY(400%);
  background-color: #c6c6c6;
  position: relative;
  width: 100%;
  height: 20%;
  animation: pour-tea 2s 1s forwards;
  z-index: 2;
}
</style>