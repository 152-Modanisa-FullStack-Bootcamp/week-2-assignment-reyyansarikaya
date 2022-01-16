<template>
  <div class="favoriteMain">
    <Header class="header"></Header>
    <Video id="video"
        v-for="video in filteredVideos"
        :video="video"
        :key="video.id"
    />
  </div>

</template>

<script>
import axios from "axios";
import Video from "../components/Video";
import Header from "../components/Header";
export default {
  name: "FavoritePage",
  components:{
    Video,
    Header
  },
  data() {
    return {
      videos: []
    }
  },
  computed:{
    filteredVideos(){
      return this.videos.filter(video=>video.favorite)
    }
  },
  async mounted() {
    this.videos = await axios.get("https://my-json-server.typicode.com/modanisa/bootcamp-video-db/videos").then(res => res.data)
    console.log(this.videos)
  }
}
</script>

<style scoped>
.favoriteMain{
  display: flex;
  flex-direction: column;
  justify-content: center;
  width: 1000px;
  margin-top: 30px;
}

#video{
  display: flex;
  flex-wrap: wrap;
  margin-left: 50px;


}
</style>