<script lang="ts" setup>
import { ref, unref } from "vue";
import { Item } from "@/types/item";
import { LEFT_ITEMS, RIGHT_ITEMS } from "@/data/mockData";
import UiItem from "@/components/UiItem.vue";

const selectedItems = ref<Item[]>([]);
const selectedItem = ref<Item | null>(null);

const selectItem = (item: Item): void => {
  selectedItem.value = item;
};

const selectItemForCollection = (item: Item): void => {
  if (unref(selectedItems).length >= 6) {
    alert("No more than 6 items");
    return;
  }

  unref(selectedItems).push(item);
};
</script>

<template>
  <div class="board">
    <div class="board__header">
      <div class="board__items-container">
        <UiItem v-for="item in selectedItems" :key="item.id" :item="item" />
      </div>
      <div class="board__item-container">
        <UiItem v-if="selectedItem" :item="selectedItem" />
      </div>
    </div>
    <div class="board__body">
      <div class="board__items-column">
        <UiItem
          v-for="item in LEFT_ITEMS"
          :key="item.id"
          :item="item"
          @click="selectItemForCollection(item)"
        />
      </div>
      <div class="board__items-column">
        <UiItem
          v-for="item in RIGHT_ITEMS"
          :key="item.id"
          :item="item"
          @click="selectItem(item)"
        />
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.board {
  display: flex;
  flex-direction: column;
  gap: 20px;
  padding: 20px;
  width: 100%;

  &__header {
    display: flex;
    justify-content: space-between;
    width: 100%;
    gap: 20px;
  }

  &__item-container {
    padding: 10px;
    width: calc((100% - 20px) / 2);
    min-height: 200px;
    border-radius: 10px;
    box-shadow: 0 0px 5px 0px rgba(7, 74, 208, 0.6);
  }

  &__items-container {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
    padding: 10px;
    width: calc((100% - 20px) / 2);
    min-height: 200px;
    border-radius: 10px;
    box-shadow: 0 0px 5px 0px rgba(7, 208, 17, 0.6);
  }

  &__body {
    display: flex;
    justify-content: space-between;
    width: 100%;
  }

  &__items-column {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
    width: calc((100% - 20px) / 2);
    padding: 10px;
    border-radius: 20px;
    border: 1px solid rgba(0, 0, 0, 0.3);
  }
}
</style>
