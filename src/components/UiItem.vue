<script lang="ts" setup>
import { defineProps } from "vue";
import { Item } from "@/types/item";

interface Props {
  item: Item;
}

defineProps<Props>();
</script>

<template>
  <div class="item">
    <span>id: {{ item.id }}</span
    ><span>name: {{ item.name }}</span>
  </div>
</template>

<style lang="scss" scoped>
.item {
  display: flex;
  flex-direction: column;
  gap: 8px;
  padding: 8px;
  width: 150px;
  height: 80px;
  border-radius: 8px;
  box-shadow: 0 0 5px 0 rgba(0, 0, 0, 0.3);
  cursor: pointer;
  transition: all 0.3s;

  &:hover {
    box-shadow: 0 30px 30px 0 rgba(3, 12, 22, 0.1);
  }
}
</style>
