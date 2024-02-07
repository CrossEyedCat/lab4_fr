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
        <input type="text" id="songVisitors" v-model="songData.Visitors_count" />
      </div>
      <div>
        <label for="songReleaseDate">Дата выпуска (YYYY-MM-DD):</label>
        <input type="date" id="songReleaseDate" v-model="songData.release_date" />
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
        Visitors_count: "",
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
    saveSong(songData) {
      // Ваш код для отправки запроса с использованием axios
      return axios.post("http://localhost:10234/save_songs", {
        id: songData.id,
        gener: songData.gener,
        name: songData.name,
        musician: songData.musician,
        text: songData.text,
        level_id: songData.level_id,
        Visitors_count: songData.Visitors_count,
        release_date: songData.release_date,
      });
    },
  },
};
</script>