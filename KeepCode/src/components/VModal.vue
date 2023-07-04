<template>
  <div class="v-filter">
    <div>
      <button @click="openModal" class="v-filter-button">
        добавить документ
      </button>
    </div>
  </div>
</template>

<script setup>
const emit = defineEmits(["openModal"]);

const openModal = () => {
  emit("openModal");
};
</script>

<style lang="scss" scoped>
.v-filter {
  display: flex;
  justify-content: flex-end;

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
