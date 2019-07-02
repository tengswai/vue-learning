<template>
  <div id="app">
    <h1>PIXNET ALBUM</h1>
    <PhotoAlbum
      v-for="profiles in profile"
      v-bind:key="profiles.id"
      v-bind:title="profiles.title"
      v-bind:link="profiles.link"
      v-bind:thumb="profiles.thumb"
      v-on:click="showLink"
    ></PhotoAlbum>
  </div>
</template>

<script>
import PhotoAlbum from "./components/PhotoAlbum";

export default {
  name: "App",
  components: {
    PhotoAlbum
  },
  data() {
    return { profile: [] };
  },
  mounted() {
    this.$axios
      .get("https://emma.pixnet.cc/album/elements?set_id=34260&user=emmademo")
      .then(response => (this.profile = response.data.elements));
  },
  method() {
    showLink:console.log(this.link);
  }
};
</script>

<style>
h1 {
  text-align: center;
  color: #3378df;
}

img {
  margin: 10px;
  height: 200px;
  width: 200px;
  border-radius: 20px;
  border: 1px black solid;
}

ul {
  list-style: none;
}

li {
  display: inline;
  float: left;
}

span {
  display: block;
  text-align: center;
}
</style>
