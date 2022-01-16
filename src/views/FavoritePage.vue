<template>
  <div class="favoriteMain">
    <Header class="header"></Header>
    <Video id="video"
           v-for="video in videos.filter(video=>video.favorite)"
           :video="video"
           :key="video.id"

    />
  </div>

</template>

<script>
import Video from "../components/Video";
import Header from "../components/Header";
import {mapState} from 'vuex';

export default {
  name: "FavoritePage",
  components: {
    Video,
    Header
  },
  mounted() {
    this.$store.dispatch('loadVideos')
  },
  computed: mapState([
    'videos'
  ]),
}
</script>

<style scoped>
.favoriteMain {
  display: flex;
  flex-direction: column;
  justify-content: center;
  width: 1000px;
  margin-top: 30px;
}

#video {
  display: flex;
  flex-wrap: wrap;
  margin-left: 50px;
}
</style>