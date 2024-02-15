<template>
  <div>
    <h1>Тестирование запроса сохранения связи между тегом и песней</h1>
    <form @submit.prevent="submitForm">
      <div>
        <label for="tagId">ID тега:</label>
        <input type="text" id="tagId" v-model="tagSongData.tagsId" />
      </div>
      <div>
        <label for="songId">ID песни:</label>
        <input type="text" id="songId" v-model="tagSongData.songsId" />
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
      tagSongData: {
        tagsId: "",
        songsId: "",
      },
    };
  },
  methods: {
    async submitForm() {
      try {
        const response = await this.saveTagSong(this.tagSongData);
        console.log("Запрос успешно отправлен:", response.data);
      } catch (error) {
        console.error("Произошла ошибка при отправке запроса:", error);
      }
    },
    async saveTagSong(tagSongData) {
      const headers = {
        'Content-Type': 'application/json', // Указываем, что отправляем JSON
      };
      // Ваш код для отправки запроса с использованием axios
      return await axios.post(`http://localhost:10234/save_tags_songs`, tagSongData, {headers});
    },
  },
};
</script>