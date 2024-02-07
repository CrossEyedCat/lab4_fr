<template>
  <div>
    <h2>Избранные элементы пользователя</h2>
    <label for="userId">Введите идентификатор пользователя:</label>
    <input type="text" v-model="userId" id="userId" />
    <button @click="getFavorites">Получить избранные элементы</button>

    <div v-if="favorites.length > 0">
      <h3>Избранные элементы пользователя:</h3>
      <ul>
        <li v-for="item in favorites" :key="item.id">{{ item.name }}</li>
      </ul>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      userId: "",
      favorites: [],
    };
  },
  methods: {
    async getFavorites() {
      try {
        const URL = "http://localhost:10234/get_favorites";
        const data = {
          userId: this.userId
        };
        const response = await fetch(URL, {
          method: "POST",
          headers: {
            "Content-Type": "application/json",
          },
          body: JSON.stringify(data)
        });

        if (!response.ok) {
          throw new Error('Network response was not ok');
        }

        this.favorites = await response.json();
      } catch (error) {
        console.error("Ошибка при получении избранных элементов:", error);
      }
    },
  },
};
</script>

<style scoped>
/* Здесь можно добавить стили компонента */
</style>