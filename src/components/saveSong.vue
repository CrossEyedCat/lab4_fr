<template>
  <div>
    <h1>Тестирование запроса сохранения информации о песне</h1>
    <form @submit.prevent="submitForm">
      <div>
        <label for="songId">ID песни:</label>
        <input type="text" id="songId" v-model="songData.id" />
      </div>
      <div>
        <label for="songGener">Жанр:</label>
        <input type="text" id="songGener" v-model="songData.gener" />
      </div>
      <div>
        <label for="songName">Название песни:</label>
        <input type="text" id="songName" v-model="songData.name" />
      </div>
      <div>
        <label for="songMusician">Музыкант:</label>
        <input type="text" id="songMusician" v-model="songData.musician" />
      </div>
      <div>
        <label for="songText">Текст песни:</label>
        <textarea id="songText" v-model="songData.text"></textarea>
      </div>
      <div>
        <label for="songLevel">ID уровня:</label>
        <input type="text" id="songLevel" v-model="songData.level_id" />
      </div>
      <div>
        <label for="songVisitors">Количество посетителей:</label>
        <input type="text" id="songVisitors" v-model="songData.visitors_count" />
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
      songData: {
        id: "",
        gener: "",
        name: "",
        musician: "",
        text: "",
        level_id: "",
        visitors_count: "",
        release_date: "",
      },
    };
  },
  methods: {
    async submitForm() {
      try {
        const response = await this.saveSong(this.songData);
        console.log("Запрос успешно отправлен:", response.data);
      } catch (error) {
        console.error("Произошла ошибка при отправке запроса:", error);
      }
    },
    async saveSong(songData) {
      const headers = {
        'Content-Type': 'application/json', // Указываем, что отправляем JSON
      };
      // Ваш код для отправки запроса с использованием axios
      return await axios.post(`http://localhost:10234/save_songs`, songData, {headers});
    },
  },
};
</script>