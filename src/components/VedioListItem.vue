<template>
  <li class="list-group-item media" @click="onVideoSelect">
    <img class="mr-3" :src="ThumbnailsUrl" alt="" />
    <div class="media-body">
        {{ getChannelTitle }}
        <br>
        {{ video.snippet.title }}
    </div>
  </li>
</template>

<script>
export default {
  name: "VedioListItem",
  data(){
      return {
      }
  },
  computed: {
    ThumbnailsUrl() {
      return this.video.snippet.thumbnails.default.url;
    },
    getChannelTitle(){
        return this.video.snippet.channelTitle;
    }
  },
  methods: {
      onVideoSelect(){
          this.$emit('videoSelect' , this.video)
      }
  },
  props: ["video"],
};
</script>

<style lang="scss" scoped>
li {
    img {
        float: left;
    }
    &:hover{
        cursor: pointer;
        background: #eee;
    }   
}
</style>
