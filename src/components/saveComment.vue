<template>
  <div>
    <h2>Добавить комментарий</h2>
    <form @submit.prevent="submitComment">
      <div>
        <label for="id">ID:</label>
        <input type="number" id="id" v-model="commentData.id">
      </div>
      <div>
        <label for="text">Текст:</label>
        <textarea id="text" v-model="commentData.text"></textarea>
      </div>
      <div>
        <label for="date">Дата (YYYY-MM-DDTHH:mm:ssZ):</label>
        <input type="date" id="date" v-model="commentData.date">
      </div>
      <div>
        <label for="songsId">ID песни:</label>
        <input type="number" id="songsId" v-model="commentData.songsId">
      </div>
      <div>
        <label for="usersId">ID пользователя:</label>
        <input type="number" id="usersId" v-model="commentData.usersId">
      </div>
      <button type="submit">Отправить</button>
    </form>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      commentData: {
        id: '',
        text: '',
        date: '',
        songsId: '',
        usersId: ''
      }
    };
  },
  methods: {
    async submitComment() {
      const url = `http://localhost:10234/save_comment`; // URL, куда вы отправляете запрос
      const headers = {
        'Content-Type': 'application/json', // Указываем, что отправляем JSON
      };

      try {
        const response = await axios.post(url, this.commentData, { headers });
        console.log(response);
        alert('Комментарий сохранён!');
      } catch (error) {
        console.error('Ошибка:', error);
        alert('Ошибка при сохранении комментария.');
      }
    }
  }
};
</script>