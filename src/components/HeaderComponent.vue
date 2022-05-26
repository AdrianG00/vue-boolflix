<template>
  <div class="container">
    <section class="row align-items-center">
      <div class="col-6 g-0">
        <span class="logo"
          >boolFlix <sup><i class="fa-solid fa-trademark"></i></sup></span>
      </div>
      <search-bar @performSearch="search" />
    </section>
  </div>
</template>

<script>
 import {state} from '../store.js'
import axios from "axios";
import SearchBar from "./SearchBar.vue";
export default {
  name: "HeaderComponent",
  components: {
    SearchBar,
  },
  data() {
    return {
      apiKey: "552fc92f2777e8be73719badf2139fe3",
      apiPath: "https://api.themoviedb.org/3/search/",
      movies: [],
      series: [],
      loading: false,
      loadingSeries: false,
      movie:''
    };
  },

  methods: {
    getMovies(queryParams) {
      axios
        .get(this.apiPath + "movie", queryParams)
        .then((res) => {
          this.movies = res.data.results;
          this.loading = false;
          state.searchAll=[...this.series, ...this.movies]
        })
        .catch((error) => {
          console.log(error);
        });
    },
    getSeries(queryParams) {
      axios
        .get(this.apiPath + "tv", queryParams)
        .then((res) => {
          this.series = res.data.results;
          this.loadingSeries = false;
          state.searchAll=[...this.series, ...this.movies]
        })
        .catch((error) => {
          console.log(error);
        });
    },
    
    search(val) {
      this.movie = val;
      const queryParams = {
        params: {
          api_key: this.apiKey,
          query: this.movie,
          language: 'it-IT',
        },
      };
      this.loading = true;
      this.loadingSeries = true;
      this.getMovies(queryParams);
      this.getSeries(queryParams);
    },
  },
};
</script>

<style lang="scss">
@import '../styles/general.scss'; 

  .logo {
    font-size: 3em;
    color: red;

    i {
      font-size: .5em;
    }
  }

</style>