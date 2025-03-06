<script>
  import Scroller from "@sveltejs/svelte-scroller";
  import { geoMercator } from "d3-geo";
  import Map from "./Map.svelte";
  import Graph from "./Graph.svelte";
  import Title from "./Title.svelte";
  import Background from "./Background.svelte";
  import DemandMap from "./DemandMap.svelte";


  let count, index, offset, progress;
  let width, height;

  // geoJsonToFit related to Map.svelte
  let geoJsonToFit = {
    type: "FeatureCollection",
    features: [
      {
        type: "Feature",
        geometry: {
          type: "Point",
          coordinates: [1, 0],
        },
      },
      {
        type: "Feature",
        geometry: {
          type: "Point",
          coordinates: [0, 1],
        },
      },
    ],
  };

  $: projection = geoMercator().fitSize([width, height], geoJsonToFit);
</script>

<!-- SDGE and UCSD images at Top-Left Corner -->
<img src="./sdge-logo.png" alt="SDGE Logo" class="sdge-logo" />
<img src="./hdsi.png" alt="UCSD Logo" class="ucsd-logo" />

<Scroller
  top={0.0}
  bottom={1}
  threshold={0.5}
  bind:count
  bind:index
  bind:offset
  bind:progress
>
  <div class="background" slot="background" bind:clientWidth={width} bind:clientHeight={height}>
    <Title {index} />
    <Background {index} />
    <DemandMap {index} />
    <!-- <Map bind:geoJsonToFit {index} /> -->
    <!-- <Graph {index} {width} {height} {projection} /> -->
  </div>

  <div class="foreground" slot="foreground">
    <section>First section</section>
    <section>Second section</section>
    <section>Third section</section>
    <section>Fourth section</section>
    <section>Fifth section</section>
    <section>Sixth section</section>
  </div>
</Scroller>

<style>
  /* SDGE Logo Styles */
  .sdge-logo {
    position: fixed; /* Fixes the image in place */
    top: -30px; /* Positions it at the top */
    left: 20px; /* Positions it at the left */
    width: 150px; /* Adjust the width as needed */
    height: auto; /* Maintains aspect ratio */
    z-index: 10; /* Ensures the image stays on top of other elements */
  }

  .ucsd-logo {
    position: fixed; /* Fixes the image in place */
    top: 25px; /* Positions it at the top */
    right: 20px; /* Positions it at the left */
    width: 200px; /* Adjust the width as needed */
    height: auto; /* Maintains aspect ratio */
    z-index: 10; /* Ensures the image stays on top of other elements */
  }

  .background {
    width: 100%;
    height: 100vh;
    position: relative;
  }

  .foreground {
    width: 50%;
    margin: 0 auto;
    height: auto;
    position: relative;
  }

  section {
    height: 80vh;
    text-align: center;
    max-width: 750px; /* adjust at will */
    color: black;
    padding: 1em;
    margin: 0 0 2em 0;
    z-index: 1;
  }
</style>
