<script>
    export let icon; // Path to the icon image
    export let alt = "Icon"; // Alternate text for accessibility
    export let onClick = () => {}; // Callback function for the button click
  </script>
  
  <div class="icon-button" on:click={onClick}>
    <img src={icon} alt={alt} />
  </div>
  
  <style>
    .icon-button {
      background-color: #224622; /* Green background */
      border-radius: 16px; /* Rounded corners */
      width: 100px; /* Button width */
      height: 100px; /* Button height */
      display: flex; /* Flex for centering */
      justify-content: center; /* Center horizontally */
      align-items: center; /* Center vertically */
      box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.2); /* Subtle shadow */
      cursor: pointer; /* Pointer cursor */
      transition: transform 0.2s ease; /* Hover effect */
    }
  
    .icon-button:hover {
      transform: scale(1.1); /* Slightly enlarge on hover */
    }
  
    .icon-button img {
      width: 70%; /* Icon size relative to the button */
      height: 70%; /* Keep proportional */
    }
  </style>
  