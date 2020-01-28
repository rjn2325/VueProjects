<template>
  <div id="movielist">
    <!-- <li v-for="movie in movies" :key="movie.imdbID"><img :src="movie.Poster" height="200px" width="200px" />
      Movie Name:{{movie.Title}} {{movie.Year}} 
      
    </li>-->
    <div class="container">
      <div class="row">
          <MovieListItem class="col-6 col-sm-3 col-md-4" v-for="movie in movies" :movie="movie" :key="movie.imdbID" id="data" />
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { Vue, Component, Prop } from "vue-property-decorator";
import MovieListItem from "../components/MovieListItem.vue";
import "bootstrap/dist/css/bootstrap.css";
import "bootstrap-vue/dist/bootstrap-vue.css";

@Component({
  components: { MovieListItem }
})
export default class MovieList extends Vue {
  @Prop([]) movies!: Array<String>;
}
</script>

<style scoped>
#data {

  padding:0.5%;
  /* border:2px solid pink; */
}
</style>