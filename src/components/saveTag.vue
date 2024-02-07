<template>
  <div>
    <h1>Тестирование запроса сохранения информации о теге</h1>
    <form @submit.prevent="submitForm">
      <div>
        <label for="tagId">ID тега:</label>
        <input type="text" id="tagId" v-model="tagData.id" />
      </div>
      <div>
        <label for="tagName">Название тега:</label>
        <input type="text" id="tagName" v-model="tagData.name" />
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
      tagData: {
        id: "",
        name: "",
      },
    };
  },
  methods: {
    async submitForm() {
      try {
        const response = await this.saveTag(this.tagData);
        console.log("Запрос успешно отправлен:", response.data);
      } catch (error) {
        console.error("Произошла ошибка при отправке запроса:", error);
      }
    },
    saveTag(tagData) {
      // Ваш код для отправки запроса с использованием axios
      return axios.post("http://localhost:10234/save_tags", {
        id: tagData.id,
        name: tagData.name,
      });
    },
  },
};
</script>