<script>
  let showPopup = false; // Reactive state to track popup visibility

  function togglePopup() {
    showPopup = !showPopup; // Toggle the popup visibility
    console.log("Popup state toggled: ", showPopup);
  }

  function callPolice() {
    console.log("Calling the police...");
    showPopup = false; // Close the popup after confirmation
  }
</script>

<!-- Emergency Circular Button -->
<div class="emergency-button" on:click={togglePopup}>
  <img src="/emergency-icon.png" alt="Emergency Icon" />
</div>

<!-- Popup -->
{#if showPopup}
  <div class="popup-overlay">
    <div class="popup-content">
      <button class="back-button" on:click={togglePopup}>
        <img src="/back-button.png" alt="Back" class="back-icon" />
      </button>
      <div class="popup-center-content">
        <h2>Do you want to call the police?</h2>
        <img class="popup-icon" src="/emergency-icon.png" alt="Emergency Icon" />
        <div class="popup-actions">
          <button class="confirm-button" on:click={callPolice}>YES</button>
          <button class="close-button" on:click={togglePopup}>NO</button>
        </div>
      </div>
    </div>
  </div>
{/if}

<style>
  /* Circular Emergency Button Styling */
  .emergency-button {
    position: absolute;
    top: 20px;
    right: 20px;
    width: 120px;
    height: 120px;
    background-color: rgba(111, 111, 112, 0.8);
    border-radius: 50%;
    box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.3);
    display: flex;
    justify-content: center;
    align-items: center;
    cursor: pointer;
    z-index: 10;
  }

  .emergency-button img {
    width: 70px;
    height: 70px;
  }

  .emergency-button:hover {
    background-color: rgba(111, 111, 112, 1);
    transition: background-color 0.3s ease;
  }

  /* Popup Overlay Styling */
  .popup-overlay {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.5);
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 20;
  }

  /* Popup Content Styling */
  .popup-content {
    position: relative;
    background: rgba(131, 1, 1, 0.714);
    color: white;
    text-align: center;
    padding: 50px;
    border-radius: 16px;
    width: 70%; /* 70% of the screen */
    height: 70%; /* 70% of the screen */
    max-width: 800px;
    max-height: 800px;
    box-shadow: 0px 6px 8px rgba(0, 0, 0, 0.3);
    display: flex;
    flex-direction: column;
    justify-content: center; /* Centers the middle content vertically */
    align-items: center; /* Centers the middle content horizontally */
  }

  /* Popup Centered Content Styling */
  .popup-center-content {
    text-align: center;
  }

  .popup-content h2 {
    font-size: 50px; /* Larger font size */
    font-weight: bold;
    margin-bottom: 30px;
  }

  .popup-icon {
    width: 150px; /* Larger icon size */
    height: 150px;
    margin: 30px 0;
  }

  /* Back Button Styling */
  .back-button {
    position: absolute;
    top: 20px;
    left: 20px;
    background: transparent;
    border: none;
    cursor: pointer;
    padding: 0;
    width: 60px; /* Slightly smaller */
    height: 60px;
  }

  .back-icon {
    width: 100%; /* Ensure it fills the button size */
    height: 100%;
    object-fit: contain; /* Maintain the image aspect ratio */
  }

  .back-button:hover .back-icon {
    filter: brightness(0.8); /* Slightly dim the image on hover */
    transition: filter 0.2s ease;
  }

  /* Popup Buttons */
  .popup-actions {
    display: flex;
    justify-content: space-around;
    margin-top: 40px;
    gap: 30px; /* Add space between buttons */
  }

  .confirm-button,
  .close-button {
    width: 250px; /* Larger button size */
    height: 90px; /* Taller buttons */
    background: rgba(69, 45, 42, 0.891);
    color: white;
    font-size: 28px; /* Larger text */
    font-weight: bold;
    border: none;
    border-radius: 16px;
    cursor: pointer;
  }

  .confirm-button:hover {
    background: rgba(0, 128, 0, 0.8);
  }

  .close-button:hover {
    background: rgba(128, 0, 0, 0.682);
  }
</style>
