<script lang="ts">
  import MapSvg from './components/MapSvg.svelte';
  import Tooltip from './components/Tooltip.svelte';
  import type { StateClickDetail } from './components/states-data';

  let currentlyActiveStateID: string;
  let stateName: string;
  let chapterName: string;
  let chapterUrl: string;
  let tooltipHidden = true;
  let clickX: number = 0;
  let clickY: number = 0;

  const handleMapClick = (e: CustomEvent<StateClickDetail>) => {
    tooltipHidden = e.detail.id === currentlyActiveStateID && !tooltipHidden;
    currentlyActiveStateID = e.detail.id;
    stateName = e.detail.name;
    chapterName = e.detail.chapterName;
    chapterUrl = e.detail.chapterUrl;
    clickX = e.detail.clickX;
    clickY = e.detail.clickY;
  };
</script>

<main>
  <Tooltip {stateName} {chapterName} {chapterUrl} hidden={tooltipHidden} {clickX} {clickY} />
  <MapSvg on:stateclick={handleMapClick} />
</main>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
