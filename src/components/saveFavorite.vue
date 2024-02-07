<template>
  <div>
    <h1>Тестирование запроса сохранения избранных</h1>
    <form @submit.prevent="submitForm">
      <div>
        <label for="userId">ID пользователя:</label>
        <input type="text" id="userId" v-model="favoriteData.Usersid" />
      </div>
      <div>
        <label for="songId">ID песни:</label>
        <input type="text" id="songId" v-model="favoriteData.Songsid" />
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
      favoriteData: {
        Usersid: "",
        Songsid: "",
      },
    };
  },
  methods: {
    async submitForm() {
      try {
        const response = await this.saveFavorite(this.favoriteData);
        console.log("Запрос успешно отправлен:", response.data);
      } catch (error) {
        console.error("Произошла ошибка при отправке запроса:", error);
      }
    },
    saveFavorite(favoriteData) {
      // Ваш код для отправки запроса с использованием axios
      return axios.post("http://localhost:10234/save_favorites", {
        Usersid: favoriteData.Usersid,
        Songsid: favoriteData.Songsid,
      });
    },
  },
};
</script>