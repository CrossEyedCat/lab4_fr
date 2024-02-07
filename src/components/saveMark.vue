<template>
  <div>
    <h1>Тестирование запроса сохранения метки</h1>
    <form @submit.prevent="submitForm">
      <div>
        <label for="markId">ID метки:</label>
        <input type="text" id="markId" v-model="markData.id" />
      </div>
      <div>
        <label for="markReaction">Реакция:</label>
        <input type="text" id="markReaction" v-model="markData.reaction" />
      </div>
      <div>
        <label for="songId">ID песни:</label>
        <input type="text" id="songId" v-model="markData.Songsid" />
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
      markData: {
        id: "",
        reaction: "",
        Songsid: "",
      },
    };
  },
  methods: {
    async submitForm() {
      try {
        const response = await this.saveMark(this.markData);
        console.log("Запрос успешно отправлен:", response.data);
      } catch (error) {
        console.error("Произошла ошибка при отправке запроса:", error);
      }
    },
    saveMark(markData) {
      // Ваш код для отправки запроса с использованием axios
      return axios.post("http://localhost:10234/save_marks", {
        id: markData.id,
        reaction: markData.reaction,
        Songsid: markData.Songsid,
      });
    },
  },
};
</script>
