<script>
  export let location = "Clifton — Cincinnati"; // Pass location dynamically
</script>

<div class="location-tag">
  <img src="/red-location-icon.png" alt="Location Icon" class="location-icon" />
  {location}
</div>

<style>
  /* Location Tag Styling */
  .location-tag {
    position: absolute; /* Position relative to parent container */
    bottom: 20px; /* Distance from the bottom */
    right: 20px; /* Distance from the right edge */
    background-color: rgba(8, 64, 15, 0.614); /* Semi-transparent red background */
    color: white; /* White text color */
    font-size: 25px; /* Larger font size */
    font-weight: bold; /* Make the text bold */
    padding: 15px 25px; /* More padding for a larger tag */
    border-radius: 30px; /* Rounded corners */
    text-align: center; /* Center-align text */
    display: flex; /* Use flexbox for icon + text alignment */
    align-items: center; /* Vertically align icon and text */
    gap: 10px; /* Space between icon and text */
    width: fit-content; /* Only as wide as the content */
    box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.2); /* Subtle shadow for depth */
    z-index: 10; /* Ensure it's above other elements */
  }

  /* Icon Styling */
  .location-icon {
    width: 30px; /* Icon width */
    height: 40px; /* Icon height */
  }
</style>
