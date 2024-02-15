<template>
  <div>
    <h1>Тестирование запроса сохранения информации о певце песни</h1>
    <form @submit.prevent="submitForm">
      <div>
        <label for="songId">ID песни:</label>
        <input type="text" id="songId" v-model="songSingerData.songsId" />
      </div>
      <div>
        <label for="singerId">ID певца:</label>
        <input type="text" id="singerId" v-model="songSingerData.Singersid" />
      </div>
      <div>
        <label for="videoLink">Ссылка на видео:</label>
        <input type="text" id="videoLink" v-model="songSingerData.link_to_video" />
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
      songSingerData: {
        songsId: "",
        singersId: "",
        link_to_video: "",
      },
    };
  },
  methods: {
    async submitForm() {
      try {
        const response = await this.saveSongSinger(this.songSingerData);
        console.log("Запрос успешно отправлен:", response.data);
      } catch (error) {
        console.error("Произошла ошибка при отправке запроса:", error);
      }
    },
    async saveSongSinger(songSingerData) {
      const headers = {
        'Content-Type': 'application/json', // Указываем, что отправляем JSON
      };
      // Ваш код для отправки запроса с использованием axios
      return await axios.post(`http://localhost:10234/save_songs_singers`, songSingerData, {headers});
    },
  },
};
</script>