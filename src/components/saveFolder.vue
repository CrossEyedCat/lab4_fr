<template>
  <div>
    <h1>Тестирование запроса сохранения папки</h1>
    <form @submit.prevent="submitForm">
      <div>
        <label for="folderId">ID папки:</label>
        <input type="text" id="folderId" v-model="folderData.id" />
      </div>
      <div>
        <label for="folderName">Название папки:</label>
        <input type="text" id="folderName" v-model="folderData.name" />
      </div>
      <div>
        <label for="userId">ID пользователя:</label>
        <input type="text" id="userId" v-model="folderData.Usersid" />
      </div>
      <button type="submit">Отправить запрос</button>
    </form>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      folderData: {
        id: "",
        name: "",
        Usersid: "",
      },
    };
  },
  methods: {
    async submitForm() {
      try {
        const response = await this.saveFolder(this.folderData);
        console.log("Запрос успешно отправлен:", response.data);
      } catch (error) {
        console.error("Произошла ошибка при отправке запроса:", error);
      }
    },
    saveFolder(folderData) {
      // Ваш код для отправки запроса с использованием axios
      return axios.post("http://localhost:10234/save_folders", {
        id: folderData.id,
        name: folderData.name,
        Usersid: folderData.Usersid,
      });
    },
  },
};
</script>