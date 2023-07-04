<template>
  <div class="v-catalog">
    <VCatalogCard
      v-for="item in CardsArray"
      :title="item.title"
      :body="item.body"
    ></VCatalogCard>
  </div>
</template>

<script setup>
import VCatalogCard from "./VCatalogCard.vue";
import { ref, onMounted, computed } from "vue";

const cards = ref([]);
const CardsArray = computed(() => (cards.value ? cards.value.slice(0, 4) : []));

onMounted(() => {
  fetchCards();
});

async function fetchCards() {
  try {
    const response = await fetch("https://jsonplaceholder.typicode.com/posts/");
    const data = await response.json();
    cards.value = data;
    console.log("Запрос прошел, всё круто!");
  } catch (error) {
    console.error("Ошибка при запросе:", error);
  }
}
</script>

<style lang="scss" scoped>
.v-catalog {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr 1fr;
  gap: 30px;
}
</style>
