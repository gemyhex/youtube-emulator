<template>
  <div class="video-wrap" v-if="video">
      <div class="video-container">
          <iframe :src="videoUrl" />
      </div>
      <h4>{{ video.snippet.title }}</h4>
      <p>{{ video.snippet.description }}</p>
  </div>
</template>

<script>
export default {
    name: "VideoDetails",
    props: ['video'],
    computed: {
        videoUrl(){
            const { videoId } = this.video.id;
            return `https://www.youtube.com/embed/${videoId}`;
        }
    }
}
</script>

<style lang="scss" scoped>
    h4{
        font-weight: 500;
        font-size: 0.8rem;
    }
    p{
        border: 2px solid black;
        padding: 2px 5px;
        font-size: 0.8rem;
    }
    iframe{
        width: 100%;
        height: 400px;
    }
</style>