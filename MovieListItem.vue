<template>
  <div class="movielistitem pa-5">
    <div class="item">
      <a href>
        <img :src="imageURL()" class="pic" />
      </a>
      <p class="title">{{ movie.Title }}</p>
      <span class="year">Year {{ movie.Year }}</span>
    </div>
  </div>
</template>

<script lang="ts">
import { Vue, Component, Prop } from "vue-property-decorator";

@Component
export default class MovieListItem extends Vue {
  @Prop() movie!: any;

  imageURL() {
    return this.movie.Poster === "N/A"
      ? require("@/assets/images/popcorn.jpg")
      : this.movie.Poster;
  }
}
</script>

<style scoped>
.item {
  text-align: center;
  /* //background-color: aqua; */
}
.pic {
  /* border: 1px solid lightslategray;  */
  border-radius: 8px;
  width: 80%;
  height: 80%;
  padding: 1%;
  align-self: center;
}

.title {
  padding: 1%;
  color: lightgray;
  margin: 0px 30px 0px 30px;
  font-size:100%;
}

.year {
  color: grey;
  padding: 1%;
  font-size: 100%;
  margin: 0px 10px 0px 30px;
}
</style>
.
