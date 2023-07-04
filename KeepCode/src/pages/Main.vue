<template>
  <div class="main">
    <VUserInfo></VUserInfo>
    <VFilter @open-modal="openModal"></VFilter>
    <VModal v-if="isOpen"></VModal>
    <VCatalog></VCatalog>
  </div>
</template>

<script setup>
import VUserInfo from "../components/VUserInfo.vue";
import VFilter from "../components/VFilter.vue";
import VCatalog from "../components/Catalog/VCatalog.vue";
import VModal from "../components/VModal.vue";
import { ref } from "vue";

const isOpen = ref(false);

const openModal = () => {
  isOpen.value = true;
};
</script>

<style lang="scss" scoped>
.main {
  grid-area: Main;
  display: flex;
  gap: 30px;
  padding: 26px 90px;
  flex-direction: column;
}
</style>
