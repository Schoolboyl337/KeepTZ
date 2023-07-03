<template>
  <div class="top">
    <div class="top-breadcrumbs">
      Главная / Ученики / <span class="active">Документы</span>
    </div>
    <div class="top-buttons">
      <VMenuBtn v-for="item in fakeData" :key="item.id" :item="item" />
    </div>
  </div>
</template>

<script setup>
import VMenuBtn from "./VMenuBtn.vue";
const fakeData = [
  {
    id: 1,
    text: "Name_user",
    url: "/avatar.png",
  },
  {
    id: 2,
    text: null,
    url: "/log-out.svg",
  },
  {
    id: 3,
    text: null,
    url: "/settings.svg",
  },
];
</script>

<style lang="scss" scoped>
.top {
  grid-area: TopNav;

  padding: 0 90px;

  display: flex;
  justify-content: space-between;
  align-items: center;

  background-color: #fff;

  &-breadcrumbs {
    color: #0d2839;
    text-shadow: 0 2px 4px rgba(0, 0, 0, 0.25);
    font-size: 14px;
    font-weight: 300;
    cursor: pointer;

    & .active {
      color: #86939c;
    }
  }

  &-buttons {
    display: flex;
    gap: 33px;
  }
}
</style>
