<template>
  <div>
    <h1>Тестирование запроса сохранения уровня</h1>
    <form @submit.prevent="submitForm">
      <div>
        <label for="levelId">ID уровня:</label>
        <input type="text" id="levelId" v-model="levelData.id" />
      </div>
      <div>
        <label for="levelName">Название уровня:</label>
        <input type="text" id="levelName" v-model="levelData.level_name" />
      </div>
      <div>
        <label for="levelInfo">Информация о уровне:</label>
        <textarea id="levelInfo" v-model="levelData.info"></textarea>
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
      levelData: {
        id: "",
        level_name: "",
        info: "",
      },
    };
  },
  methods: {
    async submitForm() {
      try {
        const response = await this.saveLevel(this.levelData);
        console.log("Запрос успешно отправлен:", response.data);
      } catch (error) {
        console.error("Произошла ошибка при отправке запроса:", error);
      }
    },
    async saveLevel(levelData) {
      const headers = {
        'Content-Type': 'application/json', // Указываем, что отправляем JSON
      };
      // Ваш код для отправки запроса с использованием axios
      return await axios.post(`http://localhost:10234/save_levels`, levelData, {headers});
    },
  },
};
</script>