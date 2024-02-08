<template>
  <div>
    <h2>Избранные элементы пользователя</h2>
    <label for="userId">Введите идентификатор пользователя:</label>
    <input type="text" v-model="userId" id="userId" />
    <button @click="getFavorites">Получить избранные элементы</button>

    <div v-if="favorites.length > 0">
      <h3>Избранные элементы пользователя:</h3>
      {{favorites}}
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
        const URL = `http://localhost:10234/get_favorites/${this.userId}`;
        const response = await axios.post(URL);

        if (response.status !== 200) {
          throw new Error('Network response was not ok');
        }
        console.log(response.data)
        this.favorites = response.data.favorites;
        console.log(this.favorites)

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