<script>
  let showPopup = false;
  let phoneNumber = "";

  function togglePopup() {
    showPopup = !showPopup;
  }

  function addNumber(number) {
    phoneNumber += number; // Append the clicked number to the phone number
  }

  function clearNumber() {
    phoneNumber = ""; // Clear the phone number
  }

  function makeCall() {
    if (phoneNumber) {
      console.log(`Calling ${phoneNumber}...`);
      // Add any additional logic for making a call here
    }
  }
</script>

<div>
  <div class="icon-button" on:click={togglePopup}>
    <img src="phone-icon.png" alt="Phone Icon" />
  </div>

  {#if showPopup}
    <div class="popup-overlay" on:click={togglePopup}>
      <div class="popup-content" on:click|stopPropagation>
        <button class="back-button" on:click={togglePopup}>
          <img src="/back-button.png" alt="Back" class="back-icon" />
        </button>
        <h2>Need to make a call?</h2>
        <div class="display-container">
          <div class="number-display">{phoneNumber || "Enter a number"}</div>
          <button class="clear-button" on:click={clearNumber}>Clear</button>
        </div>
        <div class="keypad">
          {#each Array.from({ length: 9 }, (_, i) => i + 1) as number}
            <button class="keypad-button" on:click={() => addNumber(number)}>
              {number}
            </button>
          {/each}
          <div></div> <!-- Spacer -->
          <button class="keypad-button" on:click={() => addNumber(0)}>0</button>
          <div></div> <!-- Spacer -->
        </div>
        <button class="call-button" on:click={makeCall}>
          <img src="phone-icon.png" alt="Phone Icon" class="call-icon" />
        </button>
      </div>
    </div>
  {/if}
</div>

<style>
  .icon-button {
    position: absolute;
    background-color: rgba(8, 64, 15, 0.614);
    border-radius: 16px;
    width: 150px;
    height: 150px;
    display: flex;
    justify-content: center;
    align-items: center;
    box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.2);
    cursor: pointer;
    transition: transform 0.2s ease;
    top: 280px;
    left: 50px;
  }

  .icon-button:hover {
    transform: scale(1.1);
  }

  .icon-button img {
    width: 80%;
    height: 80%;
  }

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

  .popup-content {
    position: relative;
    background: rgba(56, 65, 133, 0.9);
    color: white;
    text-align: center;
    padding: 50px;
    border-radius: 16px;
    width: 70%;
    height: 70%;
    max-width: 800px;
    max-height: 800px;
    box-shadow: 0px 6px 8px rgba(0, 0, 0, 0.3);
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }

  .popup-content h2 {
    font-size: 50px;
    font-weight: bold;
    margin-bottom: 20px;
  }

  .display-container {
    display: flex;
    justify-content: space-between;
    align-items: center;
    width: 350px; /* Align the display with the keypad */
    background: rgba(0, 0, 0, 0.7);
    color: white;
    padding: 10px;
    border-radius: 8px;
    margin-bottom: 20px;
  }

  .number-display {
    flex: 1;
    font-size: 20px;
    padding: 10px;
    text-align: left;
  }

  .clear-button {
    background: #c9241e;
    color: white;
    border: none;
    border-radius: 8px;
    padding: 10px 20px;
    cursor: pointer;
  }

  .clear-button:hover {
    background: #86120e;
  }

  .keypad {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 15px;
    justify-items: center;
    align-items: center;
    margin-bottom: 20px;
  }

  .keypad-button {
    background: rgba(93, 31, 30, 0.9);
    color: white;
    font-size: 24px;
    font-weight: bold;
    border: none;
    border-radius: 8px;
    width: 80px;
    height: 80px;
    cursor: pointer;
    display: flex;
    justify-content: center;
    align-items: center;
    box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.2);
    transition: background-color 0.3s ease;
  }

  .keypad-button:hover {
    background: #555;
  }

  .call-button {
    background: #a9d4e1;
    border: none;
    border-radius: 50%;
    width: 80px;
    height: 80px;
    display: flex;
    justify-content: center;
    align-items: center;
    cursor: pointer;
    margin-top: 20px;
  }

  .call-button:hover {
    background: #555;
  }

  .call-icon {
    width: 150%;
    height: 100%;
  }

  .back-button {
    position: absolute;
    top: 20px;
    left: 20px;
    background: transparent;
    border: none;
    cursor: pointer;
    width: 100px;
    height: 100px;
  }

  .back-icon {
    width: 100%;
    height: 100%;
    object-fit: contain;
  }
</style>
