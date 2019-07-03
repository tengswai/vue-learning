<template>
  <div id="app">
    <h1>PIXNET ALBUM</h1>
    <AlbumComponent
      v-for="profiles in profile"
      v-if="profiles.type == 'pic'"
      :key="profiles.id"
      v-bind="profiles"
      @click="showLink"
    ></AlbumComponent>
  </div>
</template>

<script>
import AlbumComponent from "./components/AlbumComponent";

export default {
  name: "App",
  components: {
    AlbumComponent
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
    showLink: console.log(this.link);
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

span {
  display: block;
  text-align: center;
}
</style>
