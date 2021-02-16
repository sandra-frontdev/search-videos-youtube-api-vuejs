<template>
  <div>
    <h1>
      Search for video
    </h1>
    <SearchBar @termChange="onTermChange"></SearchBar>
    <VideoList :videos="videos" />
  </div>
</template>

<script>
// Npm packages imports
import axios from 'axios';

// Components imports
import SearchBar from './components/SearchBar';
import VideoList from './components/VideoList';

// Defining variables
const API_KEY = 'AIzaSyC0uzrTxV7Cf4awZqkITmjgn6JrbzRW8Xg';
const URL = 'https://www.googleapis.com/youtube/v3/search';

export default {
  name: 'App',
  components: {
    SearchBar,
    VideoList
  },
  data() {
    return {
      videos: []
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
            type: 'video',
            part: 'snippet',
            q: searchTerm
          }
        })
        .then((response) => (this.videos = response.data.items));
    }
  }
};
</script>
