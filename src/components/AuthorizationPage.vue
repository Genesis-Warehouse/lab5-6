<template>
  <div>
    <form @submit.prevent="login">
      <input type="text" v-model="formData.username" name="username" required>
      <input type="password" v-model="formData.password" name="password" required>
      <button type="submit">Войти</button>
    </form>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      formData: {
        username: '',
        password: '',
      },
    };
  },
  methods: {
    login() {
      axios.post('http://localhost:8080/api/Auth/login', this.formData)
        .then(response => {
          // Обработка успешного ответа
          console.log('Успешно вошли:', response.data);
        })
        .catch(error => {
          // Обработка ошибки
          console.error('Ошибка входа:', error);
        });
    },
  },
};
</script>