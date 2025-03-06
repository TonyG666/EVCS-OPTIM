<script>
  let mapUrl = "./Map_of_parking_lots_with_demand_scores.html";
  
  export let index;
  let isVisible = false;

  $: if (index === 2) {
    isVisible = true;
  } else {
    isVisible = false;
  }
</script>

<div
  class="demandmap"
  class:visible={isVisible}
>
  <iframe
    title="EV Charging Demand Map"
    src={mapUrl}
  ></iframe>
</div>

<style>
  .demandmap {
    position: fixed;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    text-align: center;
    opacity: 0;
    visibility: hidden;
    transition: opacity 2s, visibility 2s;
    width: 100%;
    height: 600px;
    border: 1px solid #ddd;
  }

  .demandmap.visible {
    opacity: 1;
    visibility: visible;
  }

  .demandmap iframe {
    pointer-events: auto;
  }

  .demandmap.visible:hover iframe {
    pointer-events: auto;
  }

  iframe {
    width: 100%;
    height: 100%;
    border: none;
  }
</style>