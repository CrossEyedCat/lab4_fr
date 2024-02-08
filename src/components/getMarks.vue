<template>
  <div>
    <h2>Получить оценки по идентификатору песни</h2>
    <label for="songId">Введите идентификатор песни:</label>
    <input type="text" v-model="songId" id="songId" />
    <button @click="getMarks">Получить оценки</button>

    <div v-if="marks.length > 0">
      {{marks}}}
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
            `http://localhost:10234/get_marks/${this.songId}`
        );
        this.marks = response.data.mark;
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