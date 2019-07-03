<template>
  <div @click="$emit('displaylink',link)">
    <a :data-href="link">
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
  width: 300px;
}
</style>
