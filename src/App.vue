<template>
  <div id="app">
    <h1>Автосервис</h1>
    <nav>
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </nav>
    <!-- Форма создания пользователя -->
    <user-form></user-form>
  
  <!-- Форма создания записи на обслуживание -->
  <appointment-form></appointment-form>

  <!-- Компонент для отображения доступных услуг -->
  <available-services :services="services"></available-services>
    <router-view/>
  </div>
</template>
<script>
import UserForm from './components/UserForm.vue';
import AppointmentForm from './components/AppointmentForm.vue';
import AvailableServices from './components/AvailableServices.vue';
import axios from 'axios';

export default {
  components: {
    UserForm,
    AppointmentForm,
    AvailableServices,
  },
  data() {
    return {
      services: [],
    };
  },
  mounted() {
    // Получение списка доступных услуг при загрузке компонента
    this.fetchAvailableServices();
  },
  methods: {
      async fetchAvailableServices() {
  try {
    const response = await axios.get('http://localhost:6432/api/services');
    this.services = response.data;
  } catch (error) {
    console.error(error);
  }
},
  },
};
</script>
<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}
</style>
