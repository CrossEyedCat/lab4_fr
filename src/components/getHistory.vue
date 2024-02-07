<template>
  <div>
    <h2>История пользователя</h2>
    <label for="userId">Введите идентификатор пользователя:</label>
    <input type="text" v-model="userId" id="userId" />
    <button @click="getHistory">Получить историю</button>

    <div v-if="history.length > 0">
      <h3>История пользователя:</h3>
      <ul>
        <li v-for="item in history" :key="item.id">{{ item.event }}</li>
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
      history: [],
    };
  },
  methods: {
    async getHistory() {
      try {
        const response = await axios.get(
            `http://localhost:10234/get_history?userId=${this.userId}`
        );
        this.history = response.data;
      } catch (error) {
        console.error("Ошибка при получении истории:", error);
      }
    },
  },
};
</script>

<style scoped>
/* Здесь можно добавить стили компонента */
</style>