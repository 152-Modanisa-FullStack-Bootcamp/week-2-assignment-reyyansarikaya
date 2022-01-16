<template>
  <div class="header-container">
    <img @click="navigateToMainPage" src="https://eftenimedya.com/upload/youtube-515576.jpg" alt="" class="youtube-logo">
    <span @click="navigateToFavoritePage" class="button">Favorites</span>
  </div>
</template>

<script>
export default {
  name: "Header",
  methods:{
    navigateToFavoritePage(){
      this.$router.push("/favorites/bootcamp")
    },
    navigateToMainPage(){
      this.$router.push("/")
    }
  }
}
</script>

<style scoped>
.header-container{
  padding: 10px;
  margin-top: 20px;
  border-color: red;
  border-style: groove;
  border-radius: 4px;
  display: flex;
  justify-content: space-between;
}
.youtube-logo{
  width: 120px;
  height: 60px;
}
.button{
  background-color: #a4a4a4;
  color: black;
  border: none;
  padding: 15px 20px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 18px;
  font-family: sans-serif;
  transition-duration: 0.4s;
}
.button:hover{
  background-color: rgb(255, 0, 0); /* Green */
  color: white;
}
</style>