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
        <input type="text" id="songId" v-model="markData.songsId" />
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
        songsId: "",
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
    async saveMark(markData) {
      const headers = {
        'Content-Type': 'application/json', // Указываем, что отправляем JSON
      };
      // Ваш код для отправки запроса с использованием axios
      return await axios.post(`http://localhost:10234/save_marks`, markData, {headers});
    },
  },
};
</script>
