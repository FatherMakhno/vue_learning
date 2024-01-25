<script>
import User from './components/User.vue'
  export default {
    components: { User },
    data() {
      return {
        users: [],
        userName: '',
        userPass: '',
        userEmail: ''
      }
    },
    methods: {
      sendData() {
        this.users.push({
          name: this.userName,
          pass: this.userPass,
          email: this.userEmail
        })
      },
      deleteUser(index) {
        this.users.splice(index, 1);
      }
    }
  }
</script>

<template>
  <input type="text" v-model="userName" placeholder="Имя">
  <input type="password" v-model="userPass" placeholder="Пароль">
  <input type="email" v-model="userEmail" placeholder="Email">
  <p className="error"></p>
  <button @click="sendData()">Отправить</button>
  <p>{{ users }}</p>
  <User v-for="(el, index) in users" :key="index" :user="el" :index="index" :deleteUser="deleteUser"/>
</template>

<style scoped>
  
</style>
