<script>
import axios from 'axios'

export default {
  data() {
    return {
      city: "",
      error: "",
      info: null
    }
  },
  computed: {
    cityName() {
      return "<" + this.city + ">"
    }
  },
  methods: {
    getWeather() {
      if(this.city.trim().length < 2) {
        this.error = "Название должно быть больше одного символа"
        return false
      }

      this.error = ""

      axios.get(`https://api.openweathermap.org/data/2.5/weather?q=${this.city}&units=metric&appid=ac9881ee6ec3edaea9338edadb0aac75`)
        .then(res => (this.info = res.data.main.temp))
    }
  }
}
</script>

<template>
  <div class="wrapper">
    <h1>Погодное приложение</h1>
    <p>Узнать погоду в {{ city == "" ? "вашем городе" : cityName }}</p>
    <input type="text" v-model="city" placeholder="Город">
    <button v-if="city != ''" @click="getWeather()">Получить погоду</button>
    <button disabled v-else>Введите название города</button>
    <p class="error">{{ error }}</p>
    <p v-show="info != null">{{ info }}</p>
  </div>
</template>

<style scoped>
.wrapper {
  width: 900px;
  height: 500px;
  border-radius: 50px;
  background: rgb(54, 49, 49);
  padding: 20px;
  color: aliceblue;
  text-align: center;
} 

.wrapper p {
  margin-top: 10px;  
}

.wrapper input {
  margin-top: 30px;
  background: rgb(255, 240, 213);
  border: 0;
  border-bottom: 2px solid black;
  border-radius: 10px;
  color:rgb(0, 0, 0);
  font-size: 16px;
  padding: 15px 15px;
  outline: none;
}

.wrapper button {
  background: rgb(212, 145, 0);
  color: beige;
  border-radius: 10px;
  border: 2px solid rgb(218, 187, 15);  
  padding: 10px;
  margin-left: 20px;
  cursor: pointer;
  font-size: 16px;
  font-weight: 600;
}
.wrapper button:disabled {
  background: rgb(212, 127, 0);
  cursor: not-allowed;
}

.error {
  color: red;
}
</style>
