<template>
  <div class="top">
    <div class="top-breadcrumbs">
      Главная / Ученики / <span class="active">Документы</span>
    </div>
    <div>Главная / Ученики / Документы</div>
  </div>
</template>

<script setup>
import { ref } from "vue";
</script>

<style lang="scss" scoped>
.top {
  grid-area: TopNav;

  padding: 28px 90px;

  display: flex;
  justify-content: space-between;

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
}
</style>
