<template>
  <div class="cast-list">
    <h3>Cast</h3>
    <ul>
      <li v-for="(actor, index) in cast" :key="index">
        <p>{{ actor }}</p>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'CastList',
  props: {
    cast: Array
  }
};
</script>

<style scoped>
.cast-list {
  display: flex;
  flex-direction: column;
}

.cast-list ul {
  list-style-type: none;
  padding: 0;
}

.cast-list li {
  margin-bottom: 10px;
}
</style>
