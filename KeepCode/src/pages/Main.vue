<template>
  <div class="main">
    <VUserInfo></VUserInfo>
    <VFilter></VFilter>
    <VCatalog></VCatalog>
  </div>
</template>

<script setup>
import VUserInfo from "../components/VUserInfo.vue";
import VFilter from "../components/VFilter.vue";
import VCatalog from "../components/Catalog/VCatalog.vue";
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
