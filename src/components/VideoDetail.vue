<template>
  <div v-if="video" class="col-md-8">
    <div class="embed-responsive embed-responsive-16by9" style="border: 1px red">
      <div class="videoResponsive">
        <iframe
          class="embed-responsive-item"
          v-bind:src="videoUrl"
          title="YouTube video player"
          frameborder="0"
          allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen>
        </iframe>
      </div>
    </div>
    <div class="details">
      <h4>{{ video.snippet.title }}</h4>
      <p>
        {{ video.snippet.description }}
      </p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'VideoDetail',
  props: ['video'],
  computed: {
    videoUrl() {
      // const videoId = this.video.id.videoId;
      // return 'https://www.youtube.com/embed/' + videoId;

      // Updated for ES5
      const { videoId } = this.video.id;
      return `https://www.youtube.com/embed/${videoId}`;
    }
  }
}
</script>

<style scoped>

.details {
  margin-top: 10px;
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 4px;
}

.videoResponsive {
  position: relative;
  /* This equals 16x9 */
  padding-bottom: 56.25%;
  height: 0;
}

.videoResponsive iframe {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
}

</style>
