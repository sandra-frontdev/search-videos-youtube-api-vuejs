<template>
  <div>
    <ul>
      <VideoListItem
        v-bind:video="video"
        :key="video"
        v-for="video in videos"
      ></VideoListItem>
    </ul>
  </div>
</template>

<script>
import VideoListItem from './VideoListItem';

export default {
  name: 'VideoList',
  components: {
    VideoListItem
  },
  props: {
    videos: Array
  },
  methods: {}
};
</script>

<style></style>
