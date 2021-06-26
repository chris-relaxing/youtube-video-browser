<template>
  <li class="list-group-item media"
      v-on:click="onVideoSelect">
    <img class="mr-3" v-bind:src="thumbnailURL"/>
    <div class="media-body">
      {{ video.snippet.title }}
    </div>
  </li>
</template>

<script>
export default {
  name: 'VideoListItem',
  props: ['video'],
  methods: {
    onVideoSelect() {
      // emit a vue specific event, not a regular html click event
      this.$emit('videoSelect', this.video);
    }
  },
  computed: {
    thumbnailURL() {
      return this.video.snippet.thumbnails.default.url;
    }
  }
}
</script>

<style scoped>
  li {
    display: flex;
    cursor: pointer;
  }

  li:hover {
    background-color: #eee;
  }

  img {
    margin-right: 15px;
  }

</style>
