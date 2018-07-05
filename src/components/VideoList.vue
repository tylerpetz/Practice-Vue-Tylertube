<template>
  <div class="container">
    <div class="box">
      <VideoListItem 
        v-for="video in videos"
        :video="video" 
        :key="video.etag"
        @videoSelect="onVideoSelect"
      />
    </div>
  </div>
</template>

<script>
import VideoListItem from './VideoListItem';

export default {
  name: 'VideoList',
  components: {
    VideoListItem
  },
  props: ['videos'],
  methods: {
    onVideoSelect(video) {
      this.$emit('videoSelect', video);
    }
  }
};
</script>

<style scoped>
  .container {
    max-width: 768px;
  }
</style>