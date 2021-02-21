<template>
  <div class="container">
    <h1>
      Search for video
    </h1>
    <SearchBar @termChange="onTermChange"></SearchBar>
    <VideoDetail :video="selectedVideo"></VideoDetail>
    <VideoList @videoSelect="onVideoSelect" :videos="videos" />
  </div>
</template>

<script>
// Npm packages imports
import axios from "axios";

// Components imports
import SearchBar from "./components/SearchBar";
import VideoList from "./components/VideoList";
import VideoDetail from "./components/VideoDetail";

// Defining variables
const API_KEY = "AIzaSyC0uzrTxV7Cf4awZqkITmjgn6JrbzRW8Xg";
const URL = "https://www.googleapis.com/youtube/v3/search";

export default {
  name: "App",
  components: {
    SearchBar,
    VideoList,
    VideoDetail
  },
  data() {
    return {
      videos: [],
      selectedVideo: null
    };
  },
  methods: {
    onTermChange(searchTerm) {
      console.log(API_KEY);
      console.log(this.videos);
      axios
        .get(URL, {
          params: {
            key: API_KEY,
            type: "video",
            part: "snippet",
            q: searchTerm
          }
        })
        .then((response) => (this.videos = response.data.items));
    },
    onVideoSelect(video) {
      this.selectedVideo = video;
    }
  }
};
</script>
