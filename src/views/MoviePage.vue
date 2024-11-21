<template>
  <div class="movie-page">
    <MovieHeader />
    <div v-if="loading" class="loading-message">Loading...</div>
    <div v-if="error" class="error-message">{{ error }}</div>
    <DropdownMenu />
    <MovieDetails v-if="!loading && !error" :movie="movie" />
  </div>
</template>

<script>
import axios from 'axios';
import DropdownMenu from '@/components/DropdownMenu.vue';
import MovieHeader from '@/components/MovieHeader.vue';
import MovieDetails from '@/components/MovieDetails.vue';


export default {
  name: 'MoviePage',
  components: {
    MovieHeader,
    MovieDetails,
    DropdownMenu
  },
  data() {
    return {
      movie: null,
      loading: true,
      error: null
    };
  },
  mounted() {
    this.fetchMovieData();
  },
  methods: {
    async fetchMovieData() {
      const movieId = 'tt3896198'; // Movie ID for Guardians of the Galaxy Vol. 2
      const apiKey = 'd2132124'; // Your OMDB API Key

      try {
        const response = await axios.get(`https://www.omdbapi.com/?i=${movieId}&apikey=${apiKey}`);
        
        // Check if response is OK
        if (response.data.Response === "True") {
          this.movie = response.data;
        } else {
          console.error("OMDB API Error:", response.data.Error);
          this.error = response.data.Error; // Display the error from the API
        }
      } catch (error) {
        console.error("Error fetching data:", error); // Log the error details
        this.error = 'Failed to fetch movie data';
      } finally {
        this.loading = false;
      }
    }
  }
};
</script>

<style scoped>
.loading-message {
  text-align: center;
  font-size: 1.5rem;
  color: gray;
}

.error-message {
  text-align: center;
  font-size: 1.5rem;
  color: red;
}


</style>
