<template>
  <div class="info">
    <div class="info-container">
      <div>
        <img src="/userInfo/avatar.png" alt="avatar" />
      </div>
      <div class="info-container-left">
        <div class="info-container-left-block">
          <div class="info-container-left-name">Абрамова Екатерина</div>
          <img src="/userInfo/sex.png" alt="sex" class="info-container-sex" />
        </div>
        <div class="info-container-left-block">
          <div class="socials">
            <a href="#">
              <img src="/userInfo/social-logo.svg" alt="social" />
            </a>
            <a href="#">
              <img src="/userInfo/social-logo.svg" alt="social" />
            </a>
            <a href="#">
              <img src="/userInfo/social-logo.svg" alt="social" />
            </a>
          </div>
          <a href="#" class="info-container-left-comments">Коментарии</a>
        </div>
      </div>
      <div>
        <img src="/userInfo/avatar.png" alt="avatar" />
      </div>
    </div>
  </div>
</template>

<script setup></script>

<style lang="scss" scoped>
.info {
  margin: 25px 90px;
  height: fit-content;

  background-color: #fff;
  border-radius: 10px;
  &-container {
    padding: 20px;

    display: flex;
    gap: 40px;

    &-left {
      display: flex;
      flex-direction: column;
      justify-content: space-between;

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
      }
    }
  }
}
</style>
