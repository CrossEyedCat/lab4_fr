<template>
  <div>
    <h2>Поиск уровней по имени</h2>
    <label for="levelName">Введите имя уровня:</label>
    <input type="text" v-model="levelName" id="levelName" />
    <button @click="getLevels">Поиск уровней</button>

    <div v-if="levels.length > 0">
      <h3>Результаты поиска:</h3>
      <ul>
        <li v-for="level in levels" :key="level.id">{{ level.name }}</li>
      </ul>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      levelName: "",
      levels: [],
    };
  },
  methods: {
    async getLevels() {
      try {
        const response = await axios.post(
            `http://localhost:10234/get_levels/${this.levelName}`
        );
        this.levels = response.data;
      } catch (error) {
        console.error("Ошибка при поиске уровней:", error);
      }
    },
  },
};
</script>

<style scoped>
/* Здесь можно добавить стили компонента */
</style>