<script>
  import Geolocation from '$lib/Geolocation.svelte';

  let position = null;
  let error = null;

  function handleSuccess(event) {
    position = event.detail;
    error = null;
  }

  function handleError(event) {
    error = event.detail;
    position = null;
  }
</script>

<Geolocation watch={true} on:success={handleSuccess} on:error={handleError} />

{#if position}
  <p>Latitude: {position.latitude}</p>
  <p>Longitude: {position.longitude}</p>
{:else if error}
  <p>Error: {error.message}</p>
{:else}
  <p>Getting location...</p>
{/if}