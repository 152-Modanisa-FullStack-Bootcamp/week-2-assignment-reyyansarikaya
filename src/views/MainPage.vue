<template>
  <div class="main">
    <Header></Header>
    <div id="video-list-container">
      <Video
          v-for="video in videos"
          :video="video"
          :key="video.id"
      />
    </div>

  </div>
</template>

<script>
import Header from "../components/Header";
import Video from "../components/Video";
import axios from "axios";

export default {
  name: "MainPage",
  components: {
    Header,
    Video,

  },
  data() {
    return {
      videos: []
    }
  },
  async mounted() {
    this.videos = await axios.get("https://my-json-server.typicode.com/modanisa/bootcamp-video-db/videos").then(res => res.data)
    console.log(this.videos)
  }
}
</script>

<style scoped>
.main {
  display: flex;
  flex-direction: column;
  justify-content: center;
  width: 1800px;
  margin-top: 30px;
}

#video-list-container {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  margin-top: 50px;
  width: 1800px;
  margin-bottom: 100px;
}
</style>