<template>
  <div id="app">
    <s-header>
      <s-title>TESTE</s-title>
    </s-header>
    <Search :search="state.search" @search="handleSearch" />
    <p class="App-intro">Sharing a few of our favourite movies</p>
    <div class="movies">
      <Movie v-for="movie in state.movies" :movie="movie" :key="movie.imdbID" />
    </div>
  </div>
</template>

<script>
import SHeader from "./Header/StyledHeader";
import STitle from "./Header/StyledTitle";
import Search from "./Search/Search.vue";
import Movie from "./Movie/Movie.vue";
import { useMovieApi } from "../hooks/movie-api";

export default {
  name: "app",
  components: {
    SHeader,
    STitle,
    Search,
    Movie
  },
  setup() {
    const state = useMovieApi();

    return {
      state,
      handleSearch(searchTerm) {
        state.loading = true;
        state.search = searchTerm;
      }
    };
  }
};
</script>

<style>
.app {
  text-align: center;
}

.spinner {
  height: 80px;
  margin: auto;
}
.intro {
  font-size: large;
}
/* new css for movie component */
* {
  box-sizing: border-box;
}
.movies {
  display: flex;
  flex-wrap: wrap;
  flex-direction: row;
  width: 80%;
  justify-content: space-between;
  margin: 0 auto;
}

.add-movies {
  text-align: center;
}
.add-movies button {
  font-size: 16px;
  padding: 8px;
  margin: 0 10px 30px 10px;
}
.movie {
  margin: 15px 5px;
  max-width: 25%;
  width: 20%;
  background: #333;
  color: #fff;
  text-align: center;
  border-radius: 4px;
  text-transform: uppercase;
}

.movie div img {
  width: 100%;
}
.movie-picture {
  min-height: 450px;
  padding: 5px 15px 0px 15px;
  background: #000;
}

.movie div h2 {
  font-size: 12px;
}
.errorMessage {
  margin: auto;
  font-weight: bold;
  color: rgb(161, 15, 15);
}
.search {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: center;
  margin-top: 10px;
}
input[type="submit"] {
  padding: 5px;
  background-color: transparent;
  color: black;
  border: 1px solid black;
  width: 80px;
  margin-left: 5px;
  cursor: pointer;
}
input[type="submit"]:hover {
  background-color: #282c34;
  color: antiquewhite;
}
.search > input[type="text"] {
  width: 40%;
  min-width: 170px;
}
@media screen and (min-width: 694px) and (max-width: 915px) {
  .movie {
    max-width: 33%;
  }
}
@media screen and (min-width: 652px) and (max-width: 693px) {
  .movie {
    max-width: 50%;
  }
}
@media screen and (max-width: 651px) {
  .movie {
    max-width: 100%;
    margin: auto;
  }
}
</style>
