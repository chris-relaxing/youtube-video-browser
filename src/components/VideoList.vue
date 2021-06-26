<template>
  <ul class="list-group col-md-4">
    <!-- v-bind:thumbnail="video.snippet.thumbnails.default.url"
        This is not needed since the video is already being sent
        to the child component and the url information is in the video
        object. The child can access the url via a v-bind directive.
    -->
    <VideoListItem
          v-for="video in videos"
          v-bind:video="video"
          v-bind:key="video.etag"
          v-on:videoSelect="onVideoSelect"
    ></VideoListItem>
  </ul>
</template>

<script>
import VideoListItem from './VideoListItem'

export default {
  name: 'VideoList',
  components: {
    VideoListItem
  },
  methods: {
    onVideoSelect(video) {
      this.$emit('videoSelect', video);
    }
  },
  props: {
    videos: Array
  }
  // data() {
  //   return {
  //     video: {}
  //   };
  // }
}
</script>

<style>

</style>
