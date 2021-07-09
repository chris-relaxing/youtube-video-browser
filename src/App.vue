<template>
  <div class="container">
    <!-- <SearchBar v-on:termChange="onTermChange"></SearchBar> -->
    <SearchBar @termChange="onTermChange"></SearchBar>
    <div class="row">
      <VideoDetail v-bind:video="selectedVideo" />

      <!-- v-bind:videos="videos" is equivalent to :videos="videos" -->
      <VideoList
            v-bind:videos="videos"
            v-on:videoSelect="onVideoSelect"
      />
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import SearchBar from './components/SearchBar';
import VideoList from './components/VideoList';
import VideoDetail from './components/VideoDetail';
import STORED_API_KEY from './API_KEYS.txt'

const API_KEY = STORED_API_KEY;

export default {
  name: 'App',
  components: {
    SearchBar,
    VideoList,
    VideoDetail
  },
  data () {
    return {
      videos: [],
      selectedVideo: null
    }
  },
  methods: {
    onVideoSelect(video) {
      console.log(video);
      this.selectedVideo = video;
    },

    onTermChange: function (searchTerm) {
      // console.log('searchTerm: ', searchTerm);
      axios.get('https://www.googleapis.com/youtube/v3/search', {
        params: {
          key: API_KEY,
          type: 'video',
          part: 'snippet',
          q: searchTerm
        }
      }).then(response => {
        this.videos = response.data.items
        console.log(response.data.items)
      })
    }
  }
}
</script>

<style>
.container {
  /* border: 1px dashed green; */
}
</style>
