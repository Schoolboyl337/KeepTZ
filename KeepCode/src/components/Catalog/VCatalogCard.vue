<template>
  <div class="v-catalog-card">
    <div class="v-catalog-card-container-left">
      <div class="v-catalog-card-container-left-title">
        {{ title }}
      </div>
      <div class="v-catalog-card-container-left-status">
        <div class="block">
          <div class="figura" :class="{ red: !isActive }" />
          <div class="info-container-right-block-text">
            {{ isActive ? "Активен" : "Не Активен" }}
          </div>
        </div>
      </div>
      <div class="v-catalog-card-container-left-date">
        {{ finalDate }}
      </div>
      <div class="v-catalog-card-container-left-icons">
        <a href="#">
          <img src="/edit.svg" alt="icon" />
        </a>
        <a @click="removeCard" href="#">
          <img src="/bin.svg" alt="icon" />
        </a>
        <a @click="removeCard" href="#">
          <img src="/bin.svg" alt="icon" />
        </a>
      </div>
    </div>
    <div class="v-catalog-card-container-right">
      <img src="placeholder.svg" alt="placeholder" />
    </div>
  </div>
</template>

<script setup>
import { computed, defineEmits } from "vue";
const props = defineProps({
  title: {
    type: String,
    default: null,
  },
  body: {
    type: String,
    default: null,
  },
  id: {
    type: Number,
    required: true,
  },
  date: {
    type: Object,
    default: () => ({}),
  },
});

const emit = defineEmits(["remove"]);

const removeCard = () => {
  const id = props.id;
  emit("remove", id);
};

const finalDate = computed(() => {
  if (props.date) {
    if (props.date.rangeStart && props.date.rangeEnd) {
      return `${props.date.rangeStart.replace(/-/g, ".")} - 
      ${props.date.rangeEnd.replace(/-/g, ".")}`;
    } else if (props.date.rangeStart) {
      return `${props.date.rangeStart.replace(/-/g, ".")}`;
    }
  }
});

const isActive = computed(() => props?.title?.length >= 30);
</script>

<style lang="scss" scoped>
.v-catalog-card {
  display: flex;
  justify-content: space-between;
  padding: 20px;
  align-items: center;

  border-radius: 10px;
  background-color: #fff;

  &-container-left {
    max-width: 200px;
    &-title {
      color: #0d2839;
      font-size: 24px;
      font-weight: 700;

      white-space: nowrap;
      overflow: hidden;
      text-overflow: ellipsis;
    }

    &-status {
      align-self: end;
      display: flex;
      flex-direction: column;
      & .block {
        display: flex;
        gap: 9px;
        align-items: center;
        & .figura {
          width: 9px;
          height: 9px;
          border-radius: 2px;
          background: #9ecb45;
          &.red {
            background-color: #fe6845;
          }
        }
      }
    }

    &-date {
      color: #86939c;
      font-size: 18px;
      font-weight: 400;
    }

    &-icons {
      margin-top: 20px;

      display: flex;
      flex-direction: row;
      justify-content: space-around;
    }
  }

  &-container-right {
    display: flex;
    border-radius: 10px;
    height: 58px;
    padding: 30px;
    background: #f2f5f8;
  }
}
</style>
