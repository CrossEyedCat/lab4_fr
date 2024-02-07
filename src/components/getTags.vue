<template>
  <div>
    <h2>Поиск тегов по имени</h2>
    <label for="tagName">Введите имя тега:</label>
    <input type="text" v-model="tagName" id="tagName" />
    <button @click="getTags">Поиск тегов</button>

    <div v-if="tags.length > 0">
      <h3>Результаты поиска:</h3>
      <ul>
        <li v-for="tag in tags" :key="tag.id">{{ tag.name }}</li>
      </ul>
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
        const response = await axios.post(
            `http://localhost:10234/get_tags/${this.tagName}`
        );
        this.tags = response.data;
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