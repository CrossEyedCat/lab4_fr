<template>
  <div>
    <h1>Тестирование запроса сохранения информации о певце</h1>
    <form @submit.prevent="submitForm">
      <div>
        <label for="singerId">ID певца:</label>
        <input type="text" id="singerId" v-model="singerData.id" />
      </div>
      <div>
        <label for="singerName">Имя певца:</label>
        <input type="text" id="singerName" v-model="singerData.name" />
      </div>
      <div>
        <label for="singerGender">Пол певца:</label>
        <select id="singerGender" v-model="singerData.gender">
          <option value="M">Мужской</option>
          <option value="F">Женский</option>
        </select>
      </div>
      <div>
        <label for="singerText">Дополнительная информация:</label>
        <textarea id="singerText" v-model="singerData.text"></textarea>
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
      singerData: {
        id: "",
        name: "",
        gender: "M",
        text: "",
      },
    };
  },
  methods: {
    async submitForm() {
      try {
        const response = await this.saveSinger(this.singerData);
        console.log("Запрос успешно отправлен:", response.data);
      } catch (error) {
        console.error("Произошла ошибка при отправке запроса:", error);
      }
    },
    async saveSinger(singerData) {
      // Ваш код для отправки запроса с использованием axios
      return await axios.post(`http://localhost:10234/save_singers/${singerData}`);
    },
  },
};
</script>