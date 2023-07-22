<template>
  <div class="v-catalog">
    <VCatalogCard
      v-for="item in items"
      :title="item.title"
      :id="item.id"
      :date="item.range"
      :body="item.body"
      @remove="up"
    />
  </div>
</template>

<script setup>
import VCatalogCard from "./VCatalogCard.vue";
import { defineEmits } from "vue";
defineProps({
  items: {
    type: Array,
    default: () => [],
  },
});

const emit = defineEmits(["remove"]);
const up = (id) => {
  emit("remove", id);
};
</script>

<style lang="scss" scoped>
.v-catalog {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
  gap: 30px;
}
</style>
