<template>
  <div>
    <h1>Тестирование запроса сохранения истории</h1>
    <form @submit.prevent="submitForm">
      <div>
        <label for="userId">ID пользователя:</label>
        <input type="text" id="userId" v-model="historyData.Usersid" />
      </div>
      <div>
        <label for="songId">ID песни:</label>
        <input type="text" id="songId" v-model="historyData.Songsid" />
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
      historyData: {
        Usersid: "",
        Songsid: "",
      },
    };
  },
  methods: {
    async submitForm() {
      try {
        const response = await this.saveHistory(this.historyData);
        console.log("Запрос успешно отправлен:", response.data);
      } catch (error) {
        console.error("Произошла ошибка при отправке запроса:", error);
      }
    },
    saveHistory(historyData) {
      // Ваш код для отправки запроса с использованием axios
      return axios.post("http://localhost:10234/save_history", {
        Usersid: historyData.Usersid,
        Songsid: historyData.Songsid,
      });
    },
  },
};
</script>