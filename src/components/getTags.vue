<template>
  <div>
    <h2>Поиск тегов по имени</h2>
    <label for="tagName">Введите имя тега:</label>
    <input type="text" v-model="tagName" id="tagName" />
    <button @click="getTags">Поиск тегов</button>

    <div v-if="tags.length > 0">
      <h3>Результаты поиска:</h3>
      {{tags}}}
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      tagName: "",
      tags: [],
    };
  },
  methods: {
    async getTags() {
      try {
        const response = await axios.get(
            `http://localhost:10234/get_tags/${this.tagName}`
        );
        this.tags = response.data.tags.length?response.data.tags:"Нет данных";
      } catch (error) {
        console.error("Ошибка при поиске тегов:", error);
      }
    },
  },
};
</script>

<style scoped>
/* Здесь можно добавить стили компонента */
</style>