<template>
  <div class="main">
    <VUserInfo></VUserInfo>
    <VFilter @sortByAlp="sortByAlp" @sortByType="sortByType" @sortByStatus="filter" @open-modal="toggleModal"></VFilter>
    <VModal v-if="isOpen" @toggle-modal="toggleModal" @on-sumbit="addCard" />
    <VCatalog @remove="deleteCard" :items="cards"></VCatalog>
  </div>
</template>

<script setup>
import VUserInfo from "../components/VUserInfo.vue";
import VFilter from "../components/VFilter.vue";
import VCatalog from "../components/Catalog/VCatalog.vue";
import VModal from "../components/VModal.vue";
import { ref, onMounted } from "vue";

const cards = ref([]);
const isOpen = ref(false);
const filterOption = ref("up");

onMounted(() => {
  fetchCards();
});

async function fetchCards() {
  try {
    const limit = 5;
    const response = await fetch(
      `https://jsonplaceholder.typicode.com/posts?_limit=${limit}`
    );
    const data = await response.json();
    cards.value = data;
  } catch (error) {
    console.error("Ошибка при запросе:", error);
  } finally {
  }
}

const toggleModal = () => {
  isOpen.value = !isOpen.value;
};

const addCard = (card) => {
  card.id = 1 + cards.value.length;
  cards.value = [...cards.value, card];
  sortByAlp();
  sortByType();
};

const deleteCard = (id) => {
  cards.value = cards.value.filter((item) => item.id !== id);
  sortByAlp();
  sortByType();
};

const sortByAlp = (option) => {
  
  if (option?.value) {
    filterOption.value = option;
    if (option.value === "up") {
      cards.value = cards.value.sort((a, b) => a.title.localeCompare(b.title));
    } else {
      cards.value = cards.value.sort((a, b) => b.title.localeCompare(a.title));
    }
  } else {
    if (filterOption.value === "up") {
      cards.value = cards.value.sort((a, b) => a.title.localeCompare(b.title));
    } else {
      cards.value = cards.value.sort((a, b) => b.title.localeCompare(a.title));
    }
  }
};

const sortByType = (option) => {
  if (option?.value) {
    option.value === "active" 
    ? cards.value = cards.value.filter( item => item.title?.length >= 30 )
    : cards.value = cards.value.filter( item => item.title?.length < 30 );
  }
}
</script>

<style lang="scss" scoped>
.main {
  grid-area: Main;
  display: flex;
  gap: 30px;
  padding: 26px 90px;
  background-color: #F2F5F8;
  flex-direction: column;
}
</style>
