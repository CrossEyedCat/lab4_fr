<template>
  <div>
    <h1>Тестирование запроса сохранения связи папки и песни</h1>
    <form @submit.prevent="submitForm">
      <div>
        <label for="folderId">ID папки:</label>
        <input type="text" id="folderId" v-model="folderSongData.foldersId" />
      </div>
      <div>
        <label for="songId">ID песни:</label>
        <input type="text" id="songId" v-model="folderSongData.songsId" />
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
      folderSongData: {
        foldersId: "",
        songsId: "",
      },
    };
  },
  methods: {
    async submitForm() {
      try {
        const response = await this.saveFolderSong(this.folderSongData);
        console.log("Запрос успешно отправлен:", response.data);
      } catch (error) {
        console.error("Произошла ошибка при отправке запроса:", error);
      }
    },
    async saveFolderSong(folderSongData) {
      const headers = {
        'Content-Type': 'application/json', // Указываем, что отправляем JSON
      };
      // Ваш код для отправки запроса с использованием axios
      return await axios.post(`http://localhost:10234/save_folders_songs`, folderSongData, {headers});
    },
  },
};
</script>