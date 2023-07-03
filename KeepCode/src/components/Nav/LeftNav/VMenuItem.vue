<template>
  <div class="item">
    <img :src="`/leftNav/${item.url}`" />
    <div class="item-text">
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
.item {
  width: 100%;
  padding: 20px 0;

  display: flex;
  flex-direction: column;
  align-items: center;
  cursor: pointer;

  &:hover {
    background: #5696ff;
  }

  & img {
    height: 30px;
    width: 30px;
  }

  &-text {
    font-size: 18px;
    font-weight: 400;
    color: #fff;
  }
}
</style>
