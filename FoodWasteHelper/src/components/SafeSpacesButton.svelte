<script>
  let showPopup = false;

  let shelters = [
    { id: 1, title: "Shelter 1", rating: 4.5, address: "123 Bellevue St", top: "20%", left: "30%" },
    { id: 2, title: "Shelter 2", rating: 5, address: "456 Short Vine St", top: "40%", left: "60%" },
    { id: 3, title: "Shelter 3", rating: 3.5, address: "3456 Eden Ave", top: "50%", left: "40%" },
    { id: 4, title: "Shelter 4", rating: 3, address: "3244 Euclid Ave", top: "70%", left: "80%" },
    { id: 5, title: "Shelter 5", rating: 4, address: "789 Short Lane", top: "30%", left: "20%" },
    { id: 6, title: "Shelter 6", rating: 2.5, address: "4567 Oak St", top: "60%", left: "10%" },
    { id: 7, title: "Shelter 7", rating: 4.5, address: "8901 Pine Ave", top: "10%", left: "50%" },
  ];

  let activeShelters = [];

  function togglePopup() {
    showPopup = !showPopup;
    if (!showPopup) {
      activeShelters = []; // Clear all active shelters when popup is closed
    }
  }

  function toggleShelter(shelterId) {
    if (activeShelters.includes(shelterId)) {
      activeShelters = activeShelters.filter(id => id !== shelterId);
    } else {
      activeShelters = [...activeShelters, shelterId];
    }
  }

  function removeShelter(shelterId) {
    activeShelters = activeShelters.filter(id => id !== shelterId);
  }
</script>

<div>
  <!-- Main Button to Toggle Popup -->
  <div class="icon-button" on:click={togglePopup}>
    <img src="safe-place-icon.png" alt="Safe Place Icon" />
  </div>

  {#if showPopup}
    <div class="popup-overlay" on:click={togglePopup}>
      <div class="popup-content" on:click|stopPropagation>
        <h2>Public Safe Spaces <br />Near You: </h2>
        <div class="carousel-container">
          <div class="stacked-buttons">
            {#each shelters as shelter}
              <button
                class="stacked-button"
                on:click={() => toggleShelter(shelter.id)}
              >
                <div class="button-content">
                  <span class="title">{shelter.title}</span>
                  <div class="details">
                    <img src="/star-icon.png" alt="Star Icon" class="star-icon" />
                    <span>{shelter.rating}</span> {shelter.address}
                  </div>
                </div>
              </button>
            {/each}
          </div>
        </div>
        <button class="close-button" on:click={togglePopup}>Close</button>
      </div>
    </div>
  {/if}

  <!-- Display Shelter Icons -->
  {#each activeShelters as shelterId}
    {#each shelters.filter(s => s.id === shelterId) as shelter}
      <div
        class="shelter-icon"
        style="top: {shelter.top}; left: {shelter.left};"
        title={shelter.title}
        on:click={() => removeShelter(shelter.id)}
      >
        <img src="shelter-location-icon.png" alt="Shelter Location" />
      </div>
    {/each}
  {/each}
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
    left: 230px;
  }

  .icon-button:hover {
    transform: scale(1.1);
  }

  .icon-button img {
    width: 100%;
    height: 100%;
  }

  .popup-overlay {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 10;
  }

  .popup-content {
    position: fixed;
    bottom: 20px;
    left: 36px;
    width: 325px;
    height: 550px;
    background: rgba(81, 42, 35, 0.9);
    color: rgb(255, 255, 255);
    border-radius: 12px;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.3);
    padding: 20px;
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    z-index: 20;
    overflow: hidden;
  }

  .popup-content h2 {
    margin-bottom: 20px;
    font-size: 20px;
    font-weight: bold;
    text-align: left;
  }

  .carousel-container {
    flex: 1;
    overflow-y: auto;
    padding-right: 10px;
    margin-bottom: 20px;
  }

  .stacked-buttons {
    display: flex;
    flex-direction: column;
    gap: 10px;
  }

  .stacked-button {
    width: 100%;
    background: rgba(255, 255, 0, 0.3);
    border: none;
    border-radius: 8px;
    padding: 10px;
    text-align: left;
    color: white;
    cursor: pointer;
    transition: background-color 0.3s ease;
  }

  .stacked-button:hover {
    background: rgba(255, 191, 15, 0.5);
  }

  .button-content .title {
    font-weight: bold;
    font-size: 16px;
    margin-bottom: 4px;
    display: block;
  }

  .button-content .details {
    font-size: 14px;
    color: #ddd;
    display: flex;
    align-items: center;
    gap: 5px;
  }

  .star-icon {
    width: 16px;
    height: 16px;
  }

  .close-button {
    align-self: flex-end;
    background: #224622;
    color: white;
    border: none;
    border-radius: 8px;
    padding: 10px 20px;
    cursor: pointer;
    font-size: 14px;
  }

  .close-button:hover {
    background: #1b371b;
  }

  .shelter-icon {
    position: absolute;
    width: 50px;
    height: 50px;
  }

  .shelter-icon img {
    width: 100%;
    height: 100%;
  }
</style>
