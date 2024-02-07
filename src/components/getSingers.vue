<template>
  <div>
    <h2>Поиск певцов по имени</h2>
    <label for="singerName">Введите имя певца:</label>
    <input type="text" v-model="singerName" id="singerName" />
    <button @click="getSingers">Поиск певцов</button>

    <div v-if="singers.length > 0">
      <h3>Результаты поиска:</h3>
      <ul>
        <li v-for="singer in singers" :key="singer.id">{{ singer.name }}</li>
      </ul>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      singerName: "",
      singers: [],
    };
  },
  methods: {
    async getSingers() {
      try {
        const response = await axios.get(
            `http://localhost:10234/get_singers?name=${this.singerName}`
        );
        this.singers = response.data;
      } catch (error) {
        console.error("Ошибка при поиске певцов:", error);
      }
    },
  },
};
</script>

<style scoped>
/* Здесь можно добавить стили компонента */
</style>