<template>
  <div>
    <h1>Тестирование запроса сохранения связи между тегом и песней</h1>
    <form @submit.prevent="submitForm">
      <div>
        <label for="tagId">ID тега:</label>
        <input type="text" id="tagId" v-model="tagSongData.Tagsid" />
      </div>
      <div>
        <label for="songId">ID песни:</label>
        <input type="text" id="songId" v-model="tagSongData.Songsid" />
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
        Tagsid: "",
        Songsid: "",
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
      // Ваш код для отправки запроса с использованием axios
      return await axios.post(`http://localhost:10234/save_tags_songs/${tagSongData}`);
    },
  },
};
</script>