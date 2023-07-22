<template>
  <div class="info">
    <div class="info-container">
      <div class="info-container-avatar">
        <img src="/userInfo/avatar.png" alt="avatar" />
      </div>
      <div class="info-container-left">
        <div class="info-container-left-block">
          <div class="info-container-left-name">Абрамова Екатерина</div>
          <div>
            <img src="/userInfo/sex.png" alt="sex" class="info-container-sex" />
          </div>
        </div>
        <div class="info-container-left-block">
          <div class="socials">
            <a v-for="index in 3" :key="`index-${index}`" href="#">
              <img src="/userInfo/social-logo.svg" alt="social" />
            </a>
          </div>
          <a href="#" class="info-container-left-comments">Коментарии</a>
        </div>
      </div>
      <div class="info-container-status">
        <div class="info-container-right-block-text title">Статус</div>
        <div class="block">
          <div class="figura" />
          <div class="info-container-right-block-text">Активен</div>
        </div>
      </div>
      <div class="info-container-right">
        <div class="info-container-right-block">
          <div v-for="item in fakeData" :key="item.id">
            <div class="info-container-right-block-text title">
              {{ item.title }}
            </div>
            <div class="info-container-right-block-text">{{ item.text }}</div>
          </div>
        </div>
      </div>
      <div class="info-container-buttons">
        <a href="#">
          <img src="/edit.svg" alt="icon" />
        </a>
        <a href="#">
          <img src="/bin.svg" alt="icon" />
        </a>
      </div>
    </div>
  </div>
</template>

<script setup>
const fakeData = [
  {
    id: 1,
    title: "Телефон",
    text: "8-900-000-00-00",
  },
  {
    id: 2,
    title: "Дата рождения",
    text: "25.04.2004 (17 лет)",
  },
  {
    id: 3,
    title: "Телефон Родителей",
    text: "8-900-000-00-00",
  },
  {
    id: 4,
    title: "Адрес",
    text: "г. Краснодар, ул. Советская 24, кв. 208",
  },
];
</script>

<style lang="scss" scoped>
.info {
  height: fit-content;

  background-color: #fff;
  border-radius: 10px;
  &-container {
    padding: 20px;
    gap: 36px;

    display: flex;
    justify-content: space-between;

    &-avatar {
      align-self: center;
    }

    &-left {
      display: flex;
      flex-direction: column;
      justify-content: space-between;
      gap: 40px;

      &-block {
        display: flex;
        align-items: center;
        gap: 30px;
      }

      & .socials {
        display: flex;
        gap: 10px;
      }

      &-comments {
        text-decoration: underline;
        font-weight: 400;
        color: #458afb;
      }

      &-name {
        color: #458afb;
        text-shadow: 0px 3px 3px rgba(0, 0, 0, 0.25);
        -webkit-text-stroke: 1px black;
        font-size: 36px;
        font-weight: 700;
        @media screen and (max-width: 1800px) {
          width: min-content;
        }
      }
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
        }
      }
    }

    &-right {
      display: flex;
      &-block {
        grid-template-columns: 1fr 1fr;
        display: grid;
        gap: 30px 10px;

        @media screen and (max-width: 1900px) {
          align-content: space-between;
        }

        &-text {
          color: #0d2839;
          font-size: 14px;
          font-weight: 400;
          &.title {
            color: #86939c;
          }
        }
      }
    }

    &-buttons {
      display: flex;
      flex-direction: column;
      justify-content: space-between;
    }
  }
}
</style>
