<template>
  <div>
    <h2>Поиск песен по имени</h2>
    <label for="songName">Введите имя песни:</label>
    <input type="text" v-model="songName" id="songName" />
    <button @click="getSongs">Поиск песен</button>

    <div v-if="songs.length > 0">
      <h3>Результаты поиска:</h3>
      <ul>
        <li v-for="song in songs" :key="song.id">{{ song.name }}</li>
      </ul>
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
        const response = await axios.post(
            `http://localhost:10234/get_songs/${this.songName}`
        );
        this.songs = response.data;
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