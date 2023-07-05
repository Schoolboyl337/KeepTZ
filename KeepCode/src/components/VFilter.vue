<template>
  <div class="v-filter">
    <div>
      <select @change="sort" v-model="option">
        <option disabled value="">Сортировать по алфавиту:</option>
        <option value="up">A - Z</option>
        <option value="down">Z - A</option>
      </select>
    </div>
    <div>
      <button @click="openModal" class="v-filter-button">
        добавить документ
      </button>
    </div>
  </div>
</template>

<script setup>
import { ref, defineEmits } from "vue";
const emit = defineEmits(["openModal", "sort"]);
const option = ref("");
const openModal = () => {
  emit("openModal");
};
const sort = () => {
  emit("sort", option);
};
</script>

<style lang="scss" scoped>
.v-filter {
  display: flex;
  justify-content: space-between;
  align-items: center;

  &-button {
    padding: 18px 10px;
    border-radius: 10px;
    background: #ffbd27;
    border-color: #ffbd27;
    cursor: pointer;

    color: #fff;
    text-align: center;
    font-size: 16px;
    font-weight: 800;
    text-transform: uppercase;
  }
}
</style>
