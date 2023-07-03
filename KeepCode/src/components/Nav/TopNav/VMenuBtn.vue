<template>
  <div class="menu-btn">
    <img :src="`/topNav/${item.url}`" />
    <div v-if="item.text" class="menu-btn-text">
      {{ item.text }}
    </div>
  </div>
</template>

<script setup>
defineProps({
  item: {
    type: Object,
    default: () => ({}),
  },
});
</script>

<style lang="scss" scoped>
.menu-btn {
  display: flex;
  justify-content: space-between;
  align-items: center;
  cursor: pointer;

  background-color: #fff;

  &:first-of-type {
    & img {
      width: 40px;
      height: 40px;
    }
  }

  &-text {
    margin-left: 10px;

    font-size: 18px;
    font-weight: 400;
    color: #0d2839;
  }
}
</style>
