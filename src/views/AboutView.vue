<template>
  <div class="about">
    <button @click="getServices">Get Services</button>
    <button @click="createUser">Create User</button>
    <button @click="createAppointment">Create Appointment</button>
  </div>
</template> 

<script>
import axios from 'axios';

export default {
  methods: {
    async getServices() {
      try {
        const response = await axios.get('http://localhost:6432/api/services');
        console.log(response.data);
      } catch (error) {
        console.error(error);
      }
    },
    async createUser() {
      try {
        const response = await axios.post('http://localhost:6432/api/users', {
          username: 'JohnDoe',
          email: 'john@example.com',
        });
        console.log(response.data);
      } catch (error) {
        console.error(error);
      }
    },
    async createAppointment() {
      try {
        const response = await axios.post('http://localhost:6432/api/appointments', {
          userId: 1,
          serviceId: 1,
          date: '2024-01-14T12:00:00Z',
        });
        console.log(response.data);
      } catch (error) {
        console.error(error);
      }
    },
  },
};
</script>
