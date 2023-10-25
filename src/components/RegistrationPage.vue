<template>
  <div class="registration-page">
    <div class="registration-form">
      <h2>Регистрация</h2>
      <form>
        <div class="input-group">
          <label for="username">Имя</label>
          <input type="text" id="username" name="username" required>
        </div>
        <div class="input-group">
          <label for="email">Почта</label>
          <input type="email" id="email" name="email" required>
        </div>
        <div class="input-group">
          <label for="password">Пароль</label>
          <input type="password" id="password" name="password" required>
        </div>
        <div class="input-group">
          <label for="confirm-password">Подтверждение пароля</label>
          <input type="password" id="confirm-password" name="confirm-password" required>
        </div>
        <button type="submit">Register</button>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: 'RegistrationPage'
}
</script>

<style scoped>
.registration-page {
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
  background-color: #8AE69D;
}

.registration-form {
  background-color: white;
  padding: 20px;
  border-radius: 10px;
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  font-family: Arial, sans-serif;
  width: 300px;
}

h2 {
  margin: 0;
  padding: 10px 0;
}

form {
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.input-group {
  width: 100%;
  display: flex;
  flex-direction: column;
  margin: 10px 0;
}

label {
  display: block;
  font-weight: bold;
  align-self: flex-start;
}

input {
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 5px;
}

button {
  background-color: #8AE69D;
  color: white;
  border: none;
  border-radius: 5px;
  padding: 10px 20px;
  cursor: pointer;
}

button:hover {
  background-color:#6DCB80;
}
</style>