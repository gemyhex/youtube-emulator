<template>
  <div class="search-wrapper">
    <input type="search" placeholder="Search Here ..." @input="onInput" />
  </div>
</template>

<script>
export default {
  name: "SearchBar",
  methods: {
    onInput(event) {
      this.$emit("onType", event.target.value);
    },
  },
};
</script>

<style lang="scss">
   .search-wrapper{
       width: 50%;
       height: 100%;
       margin-top: 20px;

        input{
            width: 80%;
            padding: 2px 8px;
            outline: none;
        }
   }
</style>
