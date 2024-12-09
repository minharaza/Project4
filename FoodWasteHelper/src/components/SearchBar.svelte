<script>
  export let placeholder = "Search..."; // Placeholder text for the search bar
</script>

<div class="search-bar">
  <!-- Search Icon -->
  <img src="/search-icon.png" alt="Search Icon" class="search-icon" />
  <!-- Search Input -->
  <input type="text" placeholder={placeholder} />
  <!-- Enter Button -->
  <button class="enter-button">
    <img src="/enter-icon.png" alt="Enter Icon" class="enter-icon" />
  </button>
</div>

<style>
  /* Search Bar Container */
  .search-bar {
    position: absolute;
    top: 20px;
    left: 20px;
    display: flex; /* Align items in a row */
    align-items: center; /* Center items vertically */
    background-color: rgba(8, 64, 15, 0.614); /* Black background with opacity */
    padding: 10px 15px; /* Padding around the content */
    border-radius: 30px; /* Rounded edges */
    box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.2); /* Subtle shadow for depth */
    width: 400px; 
    height: 30px;/* Adjusted width to fit the enter button */
    z-index: 10; /* Ensure it's above other elements */
  }

  /* Search Icon Styling */
  .search-icon {
    width: 24px; /* Icon size */
    height: 24px;
    margin-right: 10px; /* Space between icon and input */
  }

  /* Search Input Styling */
  .search-bar input {
    flex: 1; /* Take up the remaining space */
    border: none; /* Remove border */
    outline: none; /* Remove focus outline */
    background: transparent; /* Transparent background */
    color: white; /* White text */
    font-size: 25px; /* Font size */
    font-family: Arial, sans-serif; /* Font family */
    font-weight: bold; /* Make the font bold */
    padding: 5px 0; /* Adjust spacing */
  }

  /* Placeholder Text Styling */
  .search-bar input::placeholder {
    color: #ccc; /* Light gray placeholder text */
    font-size: 16px; /* Match font size */
    font-weight: bold; /* Make placeholder text bold */
  }

  /* Enter Button Styling */
  .enter-button {
    background: transparent; /* Transparent background */
    border: none; /* Remove border */
    cursor: pointer; /* Pointer cursor */
    padding: 5px; /* Add some padding */
    margin-left: 10px; /* Space between input and button */
  }

  .enter-button img {
    width: 40px; /* Icon size */
    height: 40px;
  }

  .enter-button:hover img {
    filter: brightness(1.2); /* Slightly brighten icon on hover */
    transition: filter 0.2s ease;
  }
</style>
