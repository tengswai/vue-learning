<template>
  <li>
    <a :href="link">
      <img :src="thumb">
    </a>
    <span>{{ title }}</span>
  </li>
</template>

<script>
export default {
  name: "PhotoAlbum",
  props: {
   link:String,
   thumb:String,
   title:String}
};
</script>
<style scoped>
</style>
