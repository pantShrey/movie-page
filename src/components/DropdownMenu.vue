<template>
  <div class="dropdown-menu">
    <ul class="menu">
      <!-- Overview Dropdown -->
      <li class="dropdown">
        <a href="#">Overview <i class="fa fa-chevron-down"></i></a>
        <ul class="submenu">
          <li><a href="#">Plot</a></li>
          <li><a href="#">Cast</a></li>
          <li><a href="#">Director</a></li>
        </ul>
      </li>
      
      <!-- Media Dropdown -->
      <li class="dropdown">
        <a href="#">Media <i class="fa fa-chevron-down"></i></a>
        <ul class="submenu">
          <li><a href="#">Images</a></li>
          <li><a href="#">Trailers</a></li>
          <li><a href="#">Behind the Scenes</a></li>
        </ul>
      </li>

      <!-- Fandom Dropdown -->
      <li class="dropdown">
        <a href="#">Fandom <i class="fa fa-chevron-down"></i></a>
        <ul class="submenu">
          <li><a href="#">Fan Theories</a></li>
          <li><a href="#">Fan Art</a></li>
          <li><a href="#">Discussion Forums</a></li>
        </ul>
      </li>

      <!-- Share Dropdown -->
      <li class="dropdown">
        <a href="#">Share <i class="fa fa-chevron-down"></i></a>
        <ul class="submenu">
          <li><a href="#">Facebook</a></li>
          <li><a href="#">Twitter</a></li>
          <li><a href="#">Email</a></li>
        </ul>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'DropdownMenu'
};
</script>

<style scoped>
/* Main dropdown menu styles */
.dropdown-menu {
  background-color: white;
  padding: 10px 0; /* Add vertical padding */
  position: relative;
  z-index: 10; /* Ensure the dropdown appears above other content */
  border-radius: 8px; /* Round the corners of the dropdown */
}

.menu {
  display: flex;
  justify-content: center;
  align-items: center;
  list-style-type: none;
  margin: 0;
  padding: 0;
}

.menu li {
  position: relative;
  text-align: center;
  margin-right: 20px;
}

.menu a {
  text-decoration: none;
  color: black;
  font-size: 16px;
  padding: 10px;
  transition: background-color 0.3s ease;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 8px; /* Round the corners of the menu items */
}

.menu a i {
  margin-left: 8px; /* Space between text and the arrow */
}

.menu a:hover {
  background-color: #f0f0f0; /* Light hover effect */
}

/* Dropdown arrow styles */
.fa-chevron-down {
  font-size: 10px;
}

/* Submenu styles */
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
  min-width: 150px;
  z-index: 20; /* Ensure submenu is above other content */
  border-radius: 8px; /* Round the corners of the submenu */
}

.submenu li a {
  padding: 8px 10px;
  display: block;
  text-decoration: none;
  color: black;
  border-radius: 8px; /* Round the corners of the submenu items */
}

.submenu li a:hover {
  background-color: #f0f0f0; /* Light hover effect */
}

/* Show submenu on hover */
.dropdown:hover .submenu {
  display: block;
}
</style>
