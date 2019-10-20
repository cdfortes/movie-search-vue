<template>
  <div class="movie">
    <div class="movie-picture">
      <img :alt="altText" :src="movie.Poster" />
    </div>
    <div class="movie-details">
      <h2>{{ movie.Title }}</h2>
      <p>{{ movie.Type }}</p>
      <p>{{ movie.Year }}</p>
    </div>
  </div>
</template>

<script>
import { computed } from "@vue/composition-api";

export default {
  name: "Movie",
  props: ["movie"],
  setup({ movie }) {
    const altText = computed(() => `The movie titled: ${movie.Title}`);

    return { altText };
  }
};
</script>
