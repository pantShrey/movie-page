<template>
  <header class="header">
    <div class="left-section">
      <span class="tmdb-logo">TMDB</span>
      <nav :class="{ 'nav-open': isNavOpen }">
        <ul>
          <li class="dropdown">
            <a href="#">Movies</a>
            <ul class="submenu">
              <li><a href="#">Top Rated</a></li>
              <li><a href="#">Upcoming</a></li>
              <li><a href="#">Now Playing</a></li>
              <li><a href="#">Popular</a></li>
            </ul>
          </li>
          <li class="dropdown">
            <a href="#">TV Shows</a>
            <ul class="submenu">
              <li><a href="#">Trending</a></li>
              <li><a href="#">Top Rated</a></li>
              <li><a href="#">Airing Today</a></li>
              <li><a href="#">Popular</a></li>
            </ul>
          </li>
          <li class="dropdown">
            <a href="#">People</a>
            <ul class="submenu">
              <li><a href="#">Popular People</a></li>
              <li><a href="#">Trending Celebrities</a></li>
            </ul>
          </li>
          <li class="dropdown">
            <a href="#">More</a>
            <ul class="submenu">
              <li><a href="#">Genres</a></li>
              <li><a href="#">Collections</a></li>
              <li><a href="#">Discover</a></li>
            </ul>
          </li>
        </ul>
      </nav>
    </div>
    <div class="right-section">
      <button class="add-button">+</button>
      <span class="language-selector">EN</span>
      <button class="login-button">Login</button>
      <button class="join-button">Join TMDB</button>
      <i class="fa fa-search search-icon"></i>
      <!-- Hamburger Button for Small Screens -->
      <button class="hamburger" @click="toggleNav">
        <i class="fa" :class="isNavOpen ? 'fa-times' : 'fa-bars'"></i>
      </button>
    </div>
  </header>
</template>

<script>
export default {
  name: 'MovieHeader',
  data() {
    return {
      isNavOpen: false, // State for the hamburger menu
    };
  },
  methods: {
    toggleNav() {
      this.isNavOpen = !this.isNavOpen; // Toggle navigation state
    }
  }
};
</script>

<style scoped>
.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: #2a3d66;
  color: white;
  padding: 15px 30px;
}

.left-section {
  display: flex;
  align-items: center;
  gap: 20px;
}

.tmdb-logo {
  font-weight: bold;
  font-size: 20px;
}

nav ul {
  display: flex;
  gap: 20px;
  padding: 0;
  margin: 0;
  list-style: none;
}

nav a {
  text-decoration: none;
  color: white;
  font-size: 16px;
}

.dropdown {
  position: relative;
}

.submenu {
  display: none;
  list-style-type: none;
  margin: 0;
  padding: 0;
  position: absolute;
  top: 100%;
  left: 0;
  background-color: white;
  border: 1px solid #ccc;
  border-radius: 8px;
  min-width: 150px;
  z-index: 20;
}

.submenu li a {
  padding: 8px 10px;
  display: block;
  text-decoration: none;
  color: black;
  border-radius: 8px;
}

.submenu li a:hover {
  background-color: #f0f0f0;
}

.dropdown:hover .submenu {
  display: block;
}

.right-section {
  display: flex;
  align-items: center;
  gap: 20px;
}

button {
  background-color: transparent;
  color: white;
  border: 1px solid white;
  padding: 5px 10px;
  cursor: pointer;
  border-radius: 5px;
}

.search-icon {
  font-size: 20px;
}

/* Hamburger Styles */
.hamburger {
  display: none;
  background-color: transparent;
  border: none;
  color: white;
  font-size: 24px;
  cursor: pointer;
}

@media (max-width: 768px) {
  .header {
    flex-direction: row; /* Align items in a row */
    padding: 10px 20px;
    justify-content: space-between; /* Space between items */
    align-items: center; /* Align items vertically */
  }

  .left-section, .right-section {
    width: auto;
    justify-content: space-between; /* Space between items */
    text-align: center;
    gap: 20px; /* Add space between items */
  }

  /* Show only the TMDB logo, search icon, and hamburger */
  .tmdb-logo {
    font-size: 24px;
    margin: 0;
  }

  .search-icon {
    display: inline-block; /* Keep it on the same line */
  }

  .hamburger {
    display: inline-block; /* Keep it on the same line */
  }

  /* Hide all navigation items, buttons, and other content */
  nav, .dropdown, .add-button, .language-selector, .login-button, .join-button {
    display: none; /* Hide all navigation and buttons */
  }

  /* Menu items when nav is open */
  .nav-open ul {
    display: flex; /* Show the menu when nav is open */
  }
}
</style>

