<template>
  <div id="search">
    <h3>Get to Know everything about Movie</h3>
    <input
      type="text"
      v-model="movie_name"
      @keyup.enter="showMovies()"
      placeholder="Enter movie name here"
    />
    <!-- <div class="container">
      <div class="row">
        <div  class="col-md-3" v-for="i in apidata" v-bind:key="i">
          <div class="col-md-3">Movie Name:{{i.Title}}</div>
          <div class="col-md-3">
            <img :src="i.Poster" height="200px" width="200px" />
          </div>
        </div>
      </div>
    </div> -->

    <!-- <div v-for="(element, index) in apidata" :key="index">
     
      <p v-for="(value,key ) in element" :key="key">{{key}} -{{value}}</p>
    </div>-->
  </div>
</template>

<script lang="ts">
import { Vue, Component } from "vue-property-decorator";
import axios from "axios";
const key = "f31bd18b";
const api_url = `http://www.omdbapi.com/?apikey=${key}`;
@Component
export default class Search extends Vue {
  movie_name = "";
  apidata = [];

  showMovies() {
    this.movie_name;

    axios
      .get(api_url, {
        params: {
          s: this.movie_name
        }
      })
      .then(response => {
        console.log(response);
      if(response.data.Response==='False')
        {
            console.log("Response is false :");
            return this.$emit('search',response.data.Response)
        }
        else{
          console.log("Response is true-)");
        this.apidata = response.data.Search;
        return this.$emit('search',response.data.Search);
        }
      })
      .catch(function(error) {
        console.log(error);
      });
  }
}
</script>

<style scoped>
    #search,input{
      
    font-family: inherit;
    font-weight: 700;
    background-color: transparent;
border: none;
color:white;
border-left: 0.5rem solid blue-light;
padding: 0.5rem;
width:100%;

    }
</style>