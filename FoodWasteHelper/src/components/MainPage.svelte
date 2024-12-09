<script>
  import SearchBar from "./SearchBar.svelte";
  import CurrentLocation from "./CurrentLocation.svelte";
  import Map from "./Map.svelte";
  import EmergencyButton from "./EmergencyButton.svelte";
    import PopularButton from "./PopularButton.svelte";
    import CallButton from "./CallButton.svelte";
    import SafeSpacesButton from "./SafeSpacesButton.svelte";
    import NearYou from "./NearYouButton.svelte";
    import NearYouButton from "./NearYouButton.svelte";
</script>

<div class="main-page">
  <!-- Emergency Button -->
  <EmergencyButton />

  <!-- Search Bar -->
  <SearchBar placeholder="Search something" />
  <PopularButton />
  <CallButton />
  <SafeSpacesButton />
  <NearYouButton />



  <!-- Map -->
  <Map />

  <!-- Current Location -->
  <CurrentLocation location="Clifton — Cincinnati" />
</div>

<style>
  .main-page {
    position: relative;
    width: 100vw;
    height: 100vh;
    background-image: url('/map-background.png');
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;
    overflow: hidden;
  }

  .button-panel {
    position: absolute;
    top: 150px; /* Adjust distance from the top */
    left: 20px; /* Align with search bar */
    display: grid; /* Grid layout for buttons */
    grid-template-columns: repeat(2, 1fr); /* Two columns */
    gap: 20px; /* Space between buttons */
    z-index: 10; /* Ensure above the map */
  }
</style>
