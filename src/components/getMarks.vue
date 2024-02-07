<template>
  <div>
    <h2>Получить оценки по идентификатору песни</h2>
    <label for="songId">Введите идентификатор песни:</label>
    <input type="text" v-model="songId" id="songId" />
    <button @click="getMarks">Получить оценки</button>

    <div v-if="marks.length > 0">
      <h3>Информация об оценках:</h3>
      <ul>
        <li v-for="mark in marks" :key="mark.id">{{ mark.value }}</li>
      </ul>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      songId: "",
      marks: [],
    };
  },
  methods: {
    async getMarks() {
      try {
        const response = await axios.get(
            `http://localhost:10234/get_marks?songId=${this.songId}`
        );
        this.marks = response.data;
      } catch (error) {
        console.error("Ошибка при получении оценок:", error);
      }
    },
  },
};
</script>

<style scoped>
/* Стили компонента можно добавить здесь */
</style>