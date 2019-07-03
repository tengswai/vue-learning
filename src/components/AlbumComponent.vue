<template>
  <div>
    <a :href="link">
      <img :src="thumb">
    </a>
    <span>{{ title }}</span>
  </div>
</template>

<script>
export default {
  name: "AlbumComponent",
  props: { title: "", link: "", thumb: "" }
};
</script>
<style scoped>
div {
  display: inline;
  float: left;
}
</style>
