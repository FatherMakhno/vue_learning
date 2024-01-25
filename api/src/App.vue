<script>
export default {
  data() {
    return {
      city: ""
    }
  }
}
</script>

<template>
  <div class="wrapper">
    <h1>Погодное приложение</h1>
    <p>Узнать погоду в {{ city == "" ? "вашем городе" : city }}</p>
    <input type="text" v-model="city" placeholder="Город">
    <button v-show="city != ''">Получить погоду</button>
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
</style>
