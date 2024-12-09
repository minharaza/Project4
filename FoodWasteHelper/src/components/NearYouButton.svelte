<script>
  let showPopup = false;

  // Restaurants Data
  let restaurants = [
    { id: 1, title: "Restaurant 1", rating: 4.5, address: "123 Bellevue Street", top: "15%", left: "25%" },
    { id: 2, title: "Restaurant 2", rating: 5, address: "456 Short Vine Street", top: "35%", left: "50%" },
    { id: 3, title: "Restaurant 3", rating: 3.5, address: "3456 Eden Avenue", top: "50%", left: "70%" },
    { id: 4, title: "Restaurant 4", rating: 3, address: "3244 Euclid Avenue", top: "65%", left: "30%" },
    { id: 5, title: "Restaurant 5", rating: 5, address: "789 Short Lane", top: "20%", left: "60%" },
    { id: 6, title: "Restaurant 6", rating: 2.5, address: "4567 Oak Street", top: "40%", left: "15%" },
    { id: 7, title: "Restaurant 7", rating: 4.5, address: "8901 Pine Avenue", top: "70%", left: "45%" },
  ];

  let activeRestaurants = [];

  // Toggle Popup Visibility
  function togglePopup() {
    showPopup = !showPopup;
    if (!showPopup) {
      activeRestaurants = []; // Clear all active icons when popup is closed
    }
  }

  // Toggle Individual Restaurant Icons
  function toggleRestaurant(restaurantId) {
    if (activeRestaurants.includes(restaurantId)) {
      activeRestaurants = activeRestaurants.filter(id => id !== restaurantId);
    } else {
      activeRestaurants = [...activeRestaurants, restaurantId];
    }
  }

  // Remove an Individual Icon
  function removeRestaurant(restaurantId) {
    activeRestaurants = activeRestaurants.filter(id => id !== restaurantId);
  }
</script>

<div>
  <!-- Main Button to Toggle Popup -->
  <div class="icon-button" on:click={togglePopup}>
    <img src="/dir-icon.png" alt="Near You Icon" />
  </div>

  <!-- Popup for Restaurant Details -->
  {#if showPopup}
    <div class="popup-overlay" on:click={togglePopup}>
      <div class="popup-content" on:click|stopPropagation>
        <h2>Anti-Food Waste Businesses <br />Near You:</h2>
        <div class="carousel-container">
          <div class="stacked-buttons">
            {#each restaurants as restaurant}
              <button
                class="stacked-button"
                on:click={() => toggleRestaurant(restaurant.id)}
              >
                <div class="button-content">
                  <span class="title">{restaurant.title}</span>
                  <div class="details">
                    <img src="/star-icon.png" alt="Star Icon" class="star-icon" />
                    <span>{restaurant.rating}</span> {restaurant.address}
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

  <!-- Display Restaurant Icons -->
  {#each activeRestaurants as restaurantId}
    {#each restaurants.filter(r => r.id === restaurantId) as restaurant}
      <div
        class="restaurant-icon"
        style="top: {restaurant.top}; left: {restaurant.left};"
        title={restaurant.title}
        on:click={() => removeRestaurant(restaurant.id)}
      >
        <img src="restaurants-icon.png" alt="Restaurant Location" />
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
    top: 100px;
    left: 230px;
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

  .restaurant-icon {
    position: absolute;
    width: 50px;
    height: 50px;
  }

  .restaurant-icon img {
    width: 100%;
    height: 100%;
  }
</style>
