<template>
  <div class="videos-wrapper">
    <ul class="list-group">
      <vedio-list-item
        v-for="video in videos"
        :key="video.etag"
        :video="video"
        @videoSelect="onVideoSelect"
      ></vedio-list-item>
    </ul>
  </div>
</template>

<script>
import VedioListItem from "./VedioListItem";
export default {
  name: "VedioList",
  components: {
    VedioListItem,
  },
  methods: {
      onVideoSelect(video){
          this.$emit('videoSelect' , video)
      }
  },
  props: ["videos"],
};
</script>

<style lang="scss" scoped>

</style>
