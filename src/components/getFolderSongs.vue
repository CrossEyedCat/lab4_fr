<template>
  <div>
    <h2>Песни из папки</h2>
    <label for="folderId">Введите идентификатор папки:</label>
    <input type="text" v-model="folderId" id="folderId" />
    <button @click="getFolderSongs">Получить песни из папки</button>

    <div v-if="songs.length > 0">
      <h3>Песни из выбранной папки:</h3>
      {{songs}}
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      folderId: "",
      songs: [],
    };
  },
  methods: {
    async getFolderSongs() {
      try {
        const response = await axios.get(
            `http://localhost:10234/get_folders_songs/${this.folderId}`
        );
        console.log(response.data)
        this.songs = response.data.foldersSongs;
        console.log(this.songs)
      } catch (error) {
        console.error("Ошибка при получении песен из папки:", error);
      }
    },
  },
};
</script>

<style scoped>
/* Здесь можно добавить стили компонента */
</style>