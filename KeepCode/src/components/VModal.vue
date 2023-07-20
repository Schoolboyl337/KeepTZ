<template>
  <div class="v-modal">
    <form @submit.prevent="onSubmit" class="v-modal-container">
      <div class="v-modal-header">
        <h1 class="v-modal-header-title">Добавить документ</h1>
        <img @click="toggleModal" src="/delete.svg" alt="icon" />
      </div>
      <div class="v-modal-type">
        <div class="v-modal-type-text">Тип документа:<span>*</span></div>
        <div class="v-modal-type-radiobuttons">
          <div>
            <input type="radio" id="1" value="1" v-model="document.type" />
            <label for="1">Договор</label>
          </div>
          <div>
            <input type="radio" id="2" value="2" v-model="document.type" />
            <label for="2">Справка</label>
          </div>
          <div>
            <input type="radio" id="3" value="3" v-model="document.type" />
            <label for="3">Другое</label>
          </div>
        </div>
      </div>
      <div class="v-modal-document-title">
        <input
          type="text"
          id="title"
          required
          v-model="document.title"
          placeholder="Название документа *"
        />
      </div>
      <div class="v-modal-document-number">
        <input
          type="text"
          id="number"
          v-model="document.number"
          placeholder="Номер"
        />
      </div>
      <div class="v-modal-date">
        <div>
          <label for="start">Действует с:</label>
          <input type="date" id="start" v-model="document.range.rangeStart" />
        </div>

        <div>
          <label for="end">по:</label>
          <input type="date" id="end" v-model="document.range.rangeEnd" />
        </div>
      </div>
      <div class="v-modal-checkboxes">
        <div>
          <input
            type="checkbox"
            id="alert"
            v-model="document.checkboxes.alert"
          />
          <label for="alert">Оповещать об окончании </label>
        </div>

        <div>
          <input
            type="checkbox"
            id="create"
            v-model="document.checkboxes.create"
          />
          <label for="create">Создавать задачу при окончании</label>
        </div>
      </div>
      <div class="v-modal-dropbox">
        <div
          v-if="!files.length"
          class="v-modal-dropbox-area"
          @dragenter="handleDragEnter"
          @dragleave="handleDragLeave"
          @drop="handleDrop"
          @dragover.prevent
        >
          <div class="v-modal-dropbox-area-text">
            <input type="file" ref="fileInput" @change="handleFileSelect" />
            <h2>+</h2>
            <div v-if="!isDragging">Загрузить файл</div>
            <div v-if="!isDragging">
              <span @click="upload">Выберите файл</span> или перетащите его сюда
            </div>
            <div v-else>Отпустите файлы для загрузки</div>
          </div>
        </div>
        <ol v-else>
          <li v-for="file in files" :key="file.name">{{ file.name }}</li>
        </ol>
      </div>
      <div class="v-modal-buttons">
        <button type="submit" class="v-modal-buttons-button">
          добавить документ
        </button>
        <button @click="toggleModal" class="v-modal-buttons-button gray">
          отмена
        </button>
      </div>
    </form>
  </div>
</template>

<script setup>
import { ref } from "vue";

const document = ref({
  type: null,
  title: "",
  number: null,
  range: {
    rangeStart: null,
    rangeEnd: null,
  },
  checkboxes: {
    alert: false,
    create: false,
  },
});

const fileInput = ref(null);

const files = ref([]);

let isDragging = ref(false);

function handleDragEnter(event) {
  event.preventDefault();
  isDragging.value = true;
}

function upload() {
  fileInput.value.click();
}

function handleFileSelect(event) {
  const selectedFiles = event.target.files;
  files.value = Array.from(selectedFiles);
}

function handleDragLeave(event) {
  event.preventDefault();
  isDragging.value = false;
}

function handleDrop(event) {
  event.preventDefault();
  isDragging.value = false;
  const droppedFiles = event.dataTransfer.files;
  files.value = Array.from(droppedFiles);
}

const emit = defineEmits(["toggleModal", "onSumbit"]);

const toggleModal = () => {
  emit("toggleModal");
};
const onSubmit = () => {
  const card = document.value;
  card.files = files.value;
  emit("onSumbit", card);
  toggleModal();
};
</script>

<style lang="scss" scoped>
.v-modal {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: rgba($color: #000000, $alpha: 0.5);
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 18px;



  &-container {
    display: flex;
    flex-direction: column;
    justify-content: center;
    gap: 50px;
    border-radius: 10px;
    padding: 30px;

    background: #fff;
    box-shadow: 0px 4px 5px 0px rgba(0, 0, 0, 0.1);

    @media (prefers-color-scheme: dark) {
      :root {
        background-color: black;
        color: white;
      }
    }
  }

  & span {
    color: #fe6845;
  }

  & input[type="text"] {
    width: 100%;
    border: 0;
    border-bottom: 1px solid #b9c2c9;
    &::placeholder {
      @media (prefers-color-scheme: dark) {
        color: white;
        padding-left: 5px;
      }
    }

    &:focus-visible {
      outline: none;
      border-bottom: 2px solid #7d848a;
    }
  }

  &-header {
    display: flex;
    justify-content: space-between;
    gap: 275px;

    & img {
      cursor: pointer;
    }

    &-title {
      color: #458afb;
      font-size: 36px;
      font-weight: 700;
    }
  }

  &-type {
    display: flex;
    gap: 20px;

    &-radiobuttons label {
      margin-left: 10px;
    }
  }

  &-date {
    display: flex;
    gap: 40px;
    & label {
      margin-right: 18px;
    }

    & input {
      border: 0;

      &:focus-visible {
        outline: none;
      }
    }
  }

  &-checkboxes {
    & label {
      margin-left: 10px;
    }
  }

  &-dropbox {
    &-area {
      border-radius: 10px;
      border: 1px solid #b9c2c9;
      background: #f2f5f8;
      box-shadow: 0px 4px 4px 0px rgba(0, 0, 0, 0.25);
      &-text {
        display: flex;
        flex-direction: column;
        align-items: center;
        padding: 25px;

        & span {
          text-decoration: underline;
          color: #458afb;
          cursor: pointer;
        }

        & input {
          display: none;
        }
      }
    }
    & ol {
      padding: 0 15px;
    }
  }

  &-buttons {
    display: flex;
    justify-content: center;
    gap: 30px;

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
      &.gray {
        background-color: #d5dadf;
        border-color: #d5dadf;
        width: 220px;
      }
    }
  }
}
</style>
