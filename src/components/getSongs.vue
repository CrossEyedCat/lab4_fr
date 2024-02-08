<template>
  <div>
    <h2>Поиск песен по имени</h2>
    <label for="songName">Введите имя песни:</label>
    <input type="text" v-model="songName" id="songName" />
    <button @click="getSongs">Поиск песен</button>

    <div v-if="songs.length > 0">
      <h3>Результаты поиска:</h3>
      {{songs}}
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      songName: "",
      songs: [],
    };
  },
  methods: {
    async getSongs() {
      try {
        const response = await axios.get(
            `http://localhost:10234/get_songs/${this.songName}`
        );
        this.songs = response.data.songs.length?response.data.songs:"Нет данных";
      } catch (error) {
        console.error("Ошибка при поиске песен:", error);
      }
    },
  },
};
</script>

<style scoped>
/* Здесь можно добавить стили компонента */
</style>