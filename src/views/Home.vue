<template>
  <div class="home">
    <div class="searchbar">
        <search-bar @onType="onType"></search-bar>
    </div>
    <div class="videoList">
      <vedio-list @videoSelect="onVideoSelect" :videos="videos"></vedio-list>
    </div>
    <div class="videoDetails">
      <video-details :video="selectdVideo"></video-details>
    </div>
  </div>
</template>

<style lang="scss" scoped>
  .home{
    width: 100%;
    .searchbar{
      width: 100%;
      height: 50px;
      display: flex;
      justify-content: center;
      align-items: center;
    }
    .videoList{
      width: 40%;
      float: right;
    }
    .videoDetails{
      width: 60%;
      float: left;
      display: flex;
      justify-content: center;
      align-items: center;
      padding: 20px 40px;

    }
  }
</style>

<script>
// @ is an alias to /src
import SearchBar from "../components/SearchBar";
import VedioList from "../components/VedioList";
import VideoDetails from "../components/VideoDetails";
import axios from "axios";
const API_KEY = "AIzaSyAmYuQpo7rZy-XXJADPb0DBLdcb1DpWF0I";
export default {
  name: "Home",
  data() {
    return {
      videos: [],
      clicked: false,
      selectdVideo: null
    };
  },
  components: {
    SearchBar,
    VedioList,
    VideoDetails
    
  },
  methods: {
    onVideoSelect(video){
      return this.selectdVideo = video;
    },
    onType(searchText) {
      axios
        .get("https://www.googleapis.com/youtube/v3/search", {
          params: {
            key: API_KEY,
            type: "vedio",
            part: "snippet",
            q: searchText,
          },
        })
        .then((response) => {
          this.videos = response.data.items;
        });
    },
  },
};
</script>
