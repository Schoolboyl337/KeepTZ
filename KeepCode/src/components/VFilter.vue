<template>
  <div class="v-filter">
    <div class="v-filter-sort">
      <label for="type"> Тип документа </label>
      <select id="type" @change="sortByStatus" v-model="status">
        <option disabled value="">Не выбрано</option>
        <option value="up">A - Z</option>
        <option value="down">Z - A</option>
      </select>
    </div>
    <div class="v-filter-sort">
      <label for="status"> Статус </label>
      <select id="status" @change="sortByType" v-model="type">
        <option disabled value="">Не выбрано</option>
        <option value="all">Все</option>
        <option value="active">Активные</option>
        <option value="inactive">Не Активные</option>
      </select>
    </div>
    <div class="v-filter-sort">
      <label for="filter"> Сортировать по </label>
      <select id="filter" @change="sortByAlp" v-model="filter">
        <option disabled value="">Алфaвиту</option>
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
const emit = defineEmits(["openModal", "sortByAlp", "sortByType", "sortByStatus"]);
const type = ref("");
const status = ref("");
const filter = ref("");
const openModal = () => {
  emit("openModal");
};
const sortByAlp = () => {
  emit("sortByAlp", filter);
};

const sortByType = () => {
  emit("sortByType", type);
};

const sortByStatus = () => {
  emit("sortByStatus", status);
};
</script>

<style lang="scss" scoped>
.v-filter {
  display: flex;
  justify-content: space-between;
  align-items: center;
  font-family: Alegreya Sans;

  &-sort {
    display: flex;
    gap: 5px;
    flex-direction: column;

    & label {
      color: #86939C;
    }

    & select {
      color: #458AFB;
      border: none;
      background-color: #F2F5F8;
      font-size: 18px;
      font-family: Alegreya Sans;
      &:focus-visible {
        outline: none;
      }
    }
  }

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
