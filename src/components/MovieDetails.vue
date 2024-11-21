<template>
  <section
    v-if="movie"
    class="movie-details"
    :style="{ backgroundImage: `url(${movie.Poster})` }"
  >
    <div class="overlay"></div> <!-- Semi-transparent overlay -->
    
    <div class="content">
      <!-- Left Section -->
      <div class="left-section">
        <img :src="movie.Poster" alt="Movie Poster" class="movie-poster" />
        <div class="button-group">
          <button class="watch-now">Watch Now</button>
          <button
            @click="toggleLike"
            :class="{ liked: isLiked }"
            class="like-button"
          >
            <i class="fa" :class="isLiked ? 'fa-heart' : 'fa-heart-o'"></i> Like
          </button>
        </div>
      </div>

      <!-- Right Section -->
      <div class="right-section">
        <div class="movie-header">
          <h1>{{ movie.Title }}</h1>
          <p class="rating">{{ movie.Rated }} | {{ movie.Released }} | {{ movie.Runtime }}</p>
          <p class="genres">{{ movie.Genre }}</p>
        </div>

        <!-- Score Meters -->
        <div class="score-meters">
          <ScoreMeter v-for="(score, index) in movie.Ratings" :key="index" :score="score" />
        </div>

        <!-- Movie Plot -->
        <p class="plot">{{ movie.Plot }}</p>

        <!-- Cast Section -->
        <div class="cast">
          <CastList :cast="movie.Actors.split(', ')" />
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import ScoreMeter from './ScoreMeter.vue';
import CastList from './CastList.vue';

export default {
  name: 'MovieDetails',
  components: {
    ScoreMeter,
    CastList
  },
  props: {
    movie: Object // Receive the movie data as a prop
  },
  data() {
    return {
      isLiked: false, // For the "like" functionality
    };
  },
  methods: {
    toggleLike() {
      this.isLiked = !this.isLiked; // Toggle the liked state
    }
  }
};
</script>

<style scoped>
.movie-details {
  display: flex;
  background-size: cover;
  background-position: center;
  color: white;
  padding: 50px;
  position: relative;
}

.overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(13, 28, 45, 0.8); /* Increased opacity */
  z-index: 1;
}

.content {
  z-index: 2;
  display: flex;
  width: 100%;
}

.left-section {
  width: 25%;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.movie-poster {
  width: 100%;
  height: auto;
  border-radius: 10px; /* Rounded edges for the poster */
}

.button-group {
  margin-top: 15px;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.watch-now {
  margin-bottom: 10px;
  background-color: #ff6347;
  padding: 10px;
  color: white;
  border: none;
}

.like-button {
  background-color: transparent;
  color: white;
  border: none;
  cursor: pointer;
  display: flex;
  align-items: center;
}

.like-button i {
  margin-right: 5px;
}

.liked i {
  color: red;
}

.right-section {
  width: 75%;
  padding-left: 30px;
}

.movie-header {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
}

h1 {
  font-size: 2rem;
  margin-bottom: 10px;
}

.rating {
  font-size: 1rem;
  margin: 5px 0;
}

.genres {
  font-weight: bold;
  margin: 5px 0;
}

.score-meters {
  display: flex;
  gap: 20px;
  margin-top: 20px;
}

.plot {
  margin-top: 40px; /* Increased vertical spacing */
}

.cast {
  margin-top: 20px;
}

/* Mobile-Only Layout */
@media (max-width: 768px) {
  .movie-details {
    flex-direction: column; /* Stack left and right sections vertically */
    padding: 20px; /* Reduce padding */
    background-size: contain; /* Prevent background overflow */
  }

  /* Left Section on Mobile */
  .left-section {
    width: 100%; /* Make the left section take full width */
    margin-bottom: 20px; /* Add spacing between sections */
    align-items: center; /* Center the content */
  }

  .movie-poster {
    width: 80%; /* Reduce the poster size */
    margin-bottom: 20px; /* Add margin for spacing */
  }

  .button-group {
    width: 100%;
    align-items: center;
  }

  /* Right Section on Mobile */
  .right-section {
    width: 100%; /* Make the right section take full width */
    padding: 0; /* Remove side padding */
  }

  .movie-header h1 {
    font-size: 1.5rem; /* Scale down title size */
  }

  .rating, .genres {
    font-size: 0.9rem; /* Reduce font size */
  }

  .score-meters {
    flex-wrap: wrap; /* Wrap score meters */
    justify-content: center; /* Center-align meters */
  }

  .plot {
    font-size: 0.9rem; /* Adjust plot font size */
  }

  .cast {
    font-size: 0.8rem; /* Reduce cast font size */
  }
}
</style>
