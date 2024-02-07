<template>
  <div>
    <h2>Исполнители песни</h2>
    <label for="songId">Введите идентификатор песни:</label>
    <input type="text" v-model="songId" id="songId" />
    <button @click="getSongSingers">Получить исполнителей песни</button>

    <div v-if="singers.length > 0">
      <h3>Исполнители выбранной песни:</h3>
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
      songId: "",
      singers: [],
    };
  },
  methods: {
    async getSongSingers() {
      try {
        const response = await axios.post(
            `http://localhost:10234/get_songs_singers/${this.songId}`
        );
        this.singers = response.data;
      } catch (error) {
        console.error("Ошибка при получении исполнителей песни:", error);
      }
    },
  },
};
</script>

<style scoped>
/* Здесь можно добавить стили компонента */
</style>