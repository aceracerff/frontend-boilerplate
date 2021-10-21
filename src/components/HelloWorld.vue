<template>
  <div>
    <br />
    <input type="text" /><button type="submit">Submit</button>
    <br />
    <div v-for="genre in genres" :key="genre.genre_id">
      <a href="#" @click="selectGenre(genre.genre_name)">
        {{ genre.genre_name }}
      </a> 
    </div>
    <h2 v-show="selectedGenre != null">Selected Genre: {{ selectedGenre }}</h2>
  </div>
</template>

<script>
import { ref } from "vue";

export default {
  name: "HelloWorld",
  setup() {
    const selectedGenre = ref();
    const genres = ref();
    return {
      genres,
      selectedGenre,
    };
  },
  methods: {
    selectGenre(genreName) {
      this.selectedGenre = genreName;
    },
  },
  mounted() {
    fetch("api/genres")
      .then((response) => response.json())
      .then((data) => (this.genres = data));
  },
};
</script>

<style scoped>
</style>
