<template>
  <div>
  <registration-page></registration-page>
  <authorization-page></authorization-page>
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

</style>

<script>
import RegistrationPage from '@/components/RegistrationPage.vue'; // Update the path if necessary
import AuthorizationPage from '@/components/AuthorizationPage.vue'; // Update the path if necessary

export default {
  name: 'App',
  components: {
    RegistrationPage,
    AuthorizationPage
},
}
</script>