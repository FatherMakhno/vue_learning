<script>
  export default {
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
          emai: this.userEmail
        })
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
</template>

<style scoped>
  
</style>
