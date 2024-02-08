<template>
  <div>
    <h2>Песни с тегом</h2>
    <label for="tagId">Введите идентификатор тега:</label>
    <input type="text" v-model="tagId" id="tagId" />
    <button @click="getTagSongs">Получить песни с тегом</button>

    <div v-if="songs.length > 0">
      <h3>Песни с выбранным тегом:</h3>
      {{songs}}
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      tagId: "",
      songs: [],
    };
  },
  methods: {
    async getTagSongs() {
      try {
        const response = await axios.get(
            `http://localhost:10234/get_tags_songs/${this.tagId}`
        );
        this.songs = response.data.tagsSongs.length?response.data.tagsSongs:"Нет данных";
        console.log(this.songs)
      } catch (error) {
        console.error("Ошибка при получении песен с тегом:", error);
      }
    },
  },
};
</script>

<style scoped>
/* Здесь можно добавить стили компонента */
</style>