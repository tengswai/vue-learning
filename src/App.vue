<template>
  <div id="app">
    <h1>PIXNET ALBUM</h1>
    <h3>{{ url }}</h3>
    <AlbumComponent
      v-for="profiles in filterPic"
      v-bind:key="profiles.id"
      v-bind="profiles"
      @click.native="select(profiles)"
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
    return { profile: [], url: "" };
  },
  computed: {
    filterPic: function() {
      return this.profile.filter(item => item.type === "pic");
    }
  },
  mounted() {
    this.$axios
      .get("https://emma.pixnet.cc/album/elements?set_id=34260&user=emmademo")
      .then(response => (this.profile = response.data.elements));
  },

  methods: {
    select: function(profiles) {
      this.url = profiles.link;
      console.log(this.url);
      profiles.link = "#";
    }
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
