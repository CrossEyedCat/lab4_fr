<template>
  <div>
    <h2>Поиск папок по имени</h2>
    <label for="folderName">Введите имя папки:</label>
    <input type="text" v-model="folderName" id="folderName" />
    <button @click="getFolders">Поиск папок</button>

    <div v-if="folders.length > 0">
      <h3>Результаты поиска:</h3>
      {{folders}}}
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      folderName: "",
      folders: [],
    };
  },
  methods: {
    async getFolders() {
      try {
        const response = await axios.get(
            `http://localhost:10234/get_folders/${this.folderName}`
        );
        this.folders = response.data.folders;
        if (this.folders.length===0){
          this.folders = "Нет данных"
        }
      } catch (error) {
        console.error("Ошибка при поиске папок:", error);
      }
    },
  },
};
</script>

<style scoped>
/* Здесь можно добавить стили компонента */
</style>