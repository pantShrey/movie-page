<template>
  <div id="app">
    <MoviePage />
  </div>
</template>

<script>
import MoviePage from './views/MoviePage.vue';

export default {
  name: 'App',
  components: {
    MoviePage
  }
};
</script>

<style>
body {
  font-family: Arial, sans-serif;
  margin: 0;
  padding: 0;
}
</style>
