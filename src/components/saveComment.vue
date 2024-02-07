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
        <label for="data">Дата (YYYY-MM-DDTHH:mm:ssZ):</label>
        <input type="date" id="data" v-model="commentData.data">
      </div>
      <div>
        <label for="songsId">ID песни:</label>
        <input type="number" id="songsId" v-model="commentData.Songsid">
      </div>
      <div>
        <label for="usersId">ID пользователя:</label>
        <input type="number" id="usersId" v-model="commentData.Usersid">
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
        data: '',
        Songsid: '',
        Usersid: ''
      }
    };
  },
  methods: {
    async submitComment() {
      await axios.post(`http://localhost:10234/save_comment/${this.commentData}`)
          .then(response => {
            console.log(response);
            alert('Комментарий сохранён!');
          })
          .catch(error => {
            console.error('Ошибка:', error);
            alert('Ошибка при сохранении комментария.');
          });
    }
  }
};
</script>