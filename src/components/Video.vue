<template>
  <div :class="{'video-container': !isItFavoritePage(), 'video-container-favorite': isItFavoritePage()}">
    <img class="image" @mouseover.once="coverImage=hoverImage"
         @click="goToWatch" :src="coverImage"  alt="coverImage">
    <div :class="{'info': !isItFavoritePage(), 'info-favorite': isItFavoritePage()}">
      <img id="owner-image" :src="video.ownerImage" alt="ownerImage" v-if="!isItFavoritePage()">
      <div :class="{'text-area': !isItFavoritePage(), 'text-area-favorite': isItFavoritePage()}">
        <span id="title">{{video.title}}</span>
        <span id="owner-name">{{video.ownerName}}</span>
        <div class="count-date">
          <img id="owner-image-favorite" :src="video.ownerImage" alt="ownerImage" v-if="isItFavoritePage()">
          <span id="view-count">{{video.viewCount}}</span>
          <span id="date">{{video.publishDateInMonth}}</span>
        </div>
        <div id="video-description" v-if="isItFavoritePage()"> {{video.description}}</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Video",
  props:{
    video: Object
  },
  data(){
    return{
      coverImage:this.video.coverImage,
      hoverImage:this.video.hoverImage,
      videoStyle:"video-container"
    }
  },
  methods:{
    goToWatch(){
      this.$router.push({name:"watch", query:{id:this.video.id}})
    },
    isItFavoritePage: function () {
      this.videoStyle="video-container-favorite"
      const url = this.$route.params.bootcamp
      return url === "bootcamp";
    },

  } ,
  mounted() {
    console.log(this.$route.params.bootcamp)
  }
}
</script>

<style scoped>
.video-container{
  display: flex;
  flex-direction: column;
  justify-content: center;
  width: 400px;

}
.video-container-favorite{
     display: flex;
    flex-direction: row;
    justify-content: center;   
}
.image{
  margin-top: 50px;
  width: 360px;
  height: 200px;
}
.image:hover{
  background: red;
}
.info{
  margin-top: 10px;
  width: 360px;
  display: flex;
  justify-content: space-around;
  
}
.info-favorite{
 margin-top: 50px;
 margin-left: 10px;
 display: flex;
 justify-content: flex-end;
}
.text-area{
  width: 280px;
  display: flex;
  flex-direction: column;
}
.text-area-favorite{
    width: 280px;
    display: flex;
    flex-direction: column;  
}
.count-date{
  margin-top: 10px;
  width: 10px;
  display: flex;
  justify-content: flex-start;
  color: #7a7a7a;
  font-size: 15px;
}
#owner-image{
  border-radius: 50%;
  width: 36px;
  height: 36px;
}
#owner-image-favorite{
  border-radius: 50%;
  width: 36px;
  height: 36px;
  margin-right: 10px;
}
#title{
  padding-top: 3px;
  width: 310px;
  height: 40px;
  margin-right: 20px;
  font-weight: bold;
  font-family: sans-serif-bold,sans-serif;
  font-size: 16px;
}
#owner-name{
  color: #7a7a7a;
  font-size: 15px;
}
#view-count, #date{
  margin-right: 30px;
  margin-top: 10px;
}
#video-description{
  margin-top: 10px;
 color: #7a7a7a;
  width: 350px;
}
</style>