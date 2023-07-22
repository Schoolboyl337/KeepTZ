<template>
  <div class="left">
    <img class="left-logo" src="/leftNav/logo.svg" alt="logo" />
    <VMenuItem v-for="item in fakeData" :key="item.id" :item="item" />
  </div>
</template>

<script setup>
import VMenuItem from "./VMenuItem.vue";

const fakeData = [
  {
    id: 1,
    text: "Главная",
    url: "/home.svg",
  },
  {
    id: 2,
    text: "Расписание",
    url: "/calendar.svg",
  },
  {
    id: 3,
    text: "Ученики",
    url: "/boy.svg",
  },
  {
    id: 4,
    text: "Преподаватели",
    url: "/teacher.svg",
  },
  {
    id: 5,
    text: "Занятия",
    url: "/lesson.svg",
  },
  {
    id: 6,
    text: "Работодатели",
    url: "/employees.svg",
  },
];
</script>

<style lang="scss" scoped>
.left {
  grid-area: LeftNav;

  min-height: 100vh;

  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 20px;
  padding: 0 12px;

  background-color: #458afb;
  &-logo {
    padding-top: 15px;
  }
}
</style>
